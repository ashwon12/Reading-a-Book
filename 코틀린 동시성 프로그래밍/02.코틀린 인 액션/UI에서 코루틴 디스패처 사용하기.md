# ▪️UI에서 스레드 생성하기

>코루틴의 모든 내용은 백그라운드 스레드에서 실행되기 때문에 UI 업데이트는 UI에서 일어나야 한다.

## 1️⃣의존성 추가하기

```kotlin
implementation "org.jetbrains.kotlinx:kotlinx-coroutines-core:$coroutines_version"
implementation "org.jetbrains.kotlinx:kotlinx-coroutines-android:$coroutines_version"
```

## 2️⃣ UI 코루틴 디스패처 만들기

```kotlin
GlobalScope.launch(dispatcher) {
        val headlines = fetchRssHeadlines()
        val newsCount = findViewById<TextView>(R.id.newsCount)

        launch(Dispatchers.Main) {
            newsCount.text = "Found ${headlines.size} News"
        }
}
```

UI 디스패처는 1번에서 추가해준 `kotlinx-coroutines-android` 에서 나온거기 때문에 1번이 필수이다. 

## 3️⃣ 코루틴을 별도 함수로 분리하기

코드의 재사용성을 높이긴 위해선 코루틴을 별도의 함수로 분리하는 것이 좋다.

### 비동기 호출자로 감싼 동기 함수

```kotlin
override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        launch.(dispatcher){
					loadNews()
				}
    }

private fun loadNews(){
        val headlines = fetchRssHeadlines()
        val newsCount = findViewById<TextView>(R.id.newsCount)

        GlobalScope.launch(Dispatchers.Main) {
            newsCount.text = "Found ${headlines.size} News"
        }
}
```

2번의 코드를 하나의 함수로 만드는 방법. `loadNews()` 는 호출된 스레드와 같은 스레드를 사용하게 되기 때문에 어디에서 호출하는 것이 중요한 뽀인트. 

`onCreate()` 내부에서 바로 함수를 호출하는 것이 아니라 `launch()` 블록을 통해서 호출을 감싼 다음 호출하면 된다. 

- 장점 : 비동기로 실행되는 코드가 명시적으로 나타난다.
- 단점 : `loadNews()` 를 호출하는 부분이 많으면 코드가 분산되어 가시성이 떨어진다.

### 미리 정의된 디스패처를 갖는 비동기 함수

```kotlin
override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        asyncLoadNews()
    }

private fun asyncLoadNews = GlobalScope.launch() {
        val headlines = fetchRssHeadlines()
        val newsCount = findViewById<TextView>(R.id.newsCount)

        launch(Dispatchers.Main) {
            newsCount.text = "Found ${headlines.size} News"
        }
    }
```

코루틴 안에서 함수 전체가 실행될 수 있고 `[Job](https://www.notion.so/dee4b974d5a74cc8818f20e6a7bd6467)` 을 반환할 수 있는 함수의 시그니처를 규정한다. 

그 결과로 스레드와 상관없이 `launch()` 블록이 없는 상태로 호출될 수 있다.

`onCreate()` 에서 코드를 감쌀 필요 없이 어디에서든지 함수를 호출 할 수 있다.

- 장점

함수가 여러곳에서 호출될 경우 코드를 단순화한다.  

- 단점

백그라운드 스레드에서 강제로 실행되기 때문에 함수의 유연성이 줄어든다. 

코드 가독성에 있어 제대로 된 함수 이름을 지정해야 한다. 

### 유연한 디스패처를 가지는 비동기 함수

방금 전에 살펴본 두번 째 방법의 단점인 유연성을 보완하기 위해서,,,!

```kotlin
private val defDsp = newSingleThreadContext(name = "ServiceCall")
private fun asyncLoadNews(dispatcher: CoroutineDispatcher = defDsp) 
					= GlobalScope.launch(dispatcher) { ... }
```

호출자가 특정 디스패처로 코드를 실행하는 방법도 있다. 이 방법을 사용할 땐 함수에 적절한 이름을 주어야 한다.
