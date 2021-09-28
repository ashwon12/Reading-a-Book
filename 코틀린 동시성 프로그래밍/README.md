# 코틀린 동시성 프로그래밍
안드로이드 비동기 처리를 좀 더 효율적으로 하기 위해 코틀린의 동시성 프로그래밍 공부하기 시작! 

[코틀린 동시성 프로그래밍](http://www.acornpub.co.kr/book/concurrency-kotlin#kotlin) 책을 기반으로 글을 정리하였다.



<br>

## 📚 Index

#### [1장 | Hello Concurrent World!](https://github.com/ashwon12/Reading-a-Book/tree/main/%EC%BD%94%ED%8B%80%EB%A6%B0%20%EB%8F%99%EC%8B%9C%EC%84%B1%20%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D/01.%20Hello%20Concurrent%20World!)

  - [1-1. 프로세스, 스레드, 코루틴](https://github.com/ashwon12/Reading-a-Book/blob/main/%EC%BD%94%ED%8B%80%EB%A6%B0%20%EB%8F%99%EC%8B%9C%EC%84%B1%20%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D/01.%20Hello%20Concurrent%20World!/%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%EC%99%80%20%EC%8A%A4%EB%A0%88%EB%93%9C%2C%20%EC%BD%94%EB%A3%A8%ED%8B%B4%EC%9D%98%20%EA%B4%80%EA%B3%84.md)
  - [1-2. 동시성 소개](https://github.com/ashwon12/Reading-a-Book/blob/main/%EC%BD%94%ED%8B%80%EB%A6%B0%20%EB%8F%99%EC%8B%9C%EC%84%B1%20%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D/01.%20Hello%20Concurrent%20World!/%EB%8F%99%EC%8B%9C%EC%84%B1%EC%86%8C%EA%B0%9C.md)
  - [1-3. CPU 바운드와 I/O 바운드 알고리즘](https://github.com/ashwon12/Reading-a-Book/blob/main/%EC%BD%94%ED%8B%80%EB%A6%B0%20%EB%8F%99%EC%8B%9C%EC%84%B1%20%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D/01.%20Hello%20Concurrent%20World!/CPU%20%EB%B0%94%EC%9A%B4%EB%93%9C%EC%99%80%20I.O%20%EB%B0%94%EC%9A%B4%EB%93%9C%20%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98.md)
  - [1-4. 코틀린에서의 동시성](https://github.com/ashwon12/Reading-a-Book/blob/main/%EC%BD%94%ED%8B%80%EB%A6%B0%20%EB%8F%99%EC%8B%9C%EC%84%B1%20%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D/01.%20Hello%20Concurrent%20World!/%EC%BD%94%ED%8B%80%EB%A6%B0%EC%97%90%EC%84%9C%EC%9D%98%20%EB%8F%99%EC%8B%9C%EC%84%B1.md)
  - [추가로 찾아본 부분 & 궁금한 점](https://github.com/ashwon12/Reading-a-Book/blob/main/%EC%BD%94%ED%8B%80%EB%A6%B0%20%EB%8F%99%EC%8B%9C%EC%84%B1%20%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D/01.%20Hello%20Concurrent%20World!/More.md)
#### [2장 | 코루틴 인 액션](https://github.com/ashwon12/Reading-a-Book/tree/main/%EC%BD%94%ED%8B%80%EB%A6%B0%20%EB%8F%99%EC%8B%9C%EC%84%B1%20%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D/02.%EC%BD%94%ED%8B%80%EB%A6%B0%20%EC%9D%B8%20%EC%95%A1%EC%85%98)
- [2-1. 들어가기 전에..](https://github.com/ashwon12/Reading-a-Book/blob/main/%EC%BD%94%ED%8B%80%EB%A6%B0%20%EB%8F%99%EC%8B%9C%EC%84%B1%20%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D/02.%EC%BD%94%ED%8B%80%EB%A6%B0%20%EC%9D%B8%20%EC%95%A1%EC%85%98/%EB%93%A4%EC%96%B4%EA%B0%80%EA%B8%B0%EC%A0%84.md)
- [2-2. 스레드 생성하기](https://github.com/ashwon12/Reading-a-Book/blob/main/%EC%BD%94%ED%8B%80%EB%A6%B0%20%EB%8F%99%EC%8B%9C%EC%84%B1%20%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D/02.%EC%BD%94%ED%8B%80%EB%A6%B0%20%EC%9D%B8%20%EC%95%A1%EC%85%98/%EC%8A%A4%EB%A0%88%EB%93%9C%20%EC%83%9D%EC%84%B1%ED%95%98%EA%B8%B0.md)
#### 3장 | 라이트 사이클과 에러 핸들링
#### 4장 | 일시 중단 함수와 코루틴 컨텍스트
#### 5장 | 이터레이터, 시퀀스 그리고 프로듀서
#### 6장 | 채널-통신을 통한 메모리 공유
#### 7장 | 스레드 한정, 액터 그리고 뮤텍스
#### 8장 | 동시성 코드 테스트와 디버깅
#### 9장 | 코틀린 동시성 내부

<br>

