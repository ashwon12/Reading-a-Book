# More

### 추가로 찾아본 부분

<details>
<summary>병목현상</summary>
<div markdown="1">       

2차선 도로가 1차선으로 바뀔때 차들이 몰려 정체되듯이, 많은 양의 데이터가 와랄라랄 모였을 때, 메모리가 이를 제대로 소화하지 못해서 성능이 떨어지게 되는 현상

</div>
</details>

<details>
<summary> 동기/비동기 & 논블로킹/블로킹</summary>
<div markdown="1">       

  - 동기/비동기

    **작업을 수행하는 주체**가 2개 이상, 수행하는 주체에 시간이 연관있으면 동기, 시간이 연관없으면 비동기

    - 논블로킹/블로킹

    **작업의 대상**이 2개 이상, 

    블로킹 : 자신의 작업을 하다가 다른 작업 주체가 하는 작업의 시작~끝을 기다렸다가 다시 자신의 작업 하기 

    논블로킹 : 다른 주체의 작업과 곤계없이 자신의 작업을 계속 하는 것

    [동기/비동기와 블로킹/논블로킹](https://deveric.tistory.com/99)
</div>
</details>


<details>
<summary> 스레드 풀</summary>
<div markdown="1">       

- 스레드 풀

    스레드는 할당되어진 메모리 영역에서 생성되고 관리되지만, 생성/수거에 드는 비용을 무시할 수 없다. 

    따라서 요청이 들어올 때마다 생성/수거 하는 작업을 한다면 퍼포먼스에 영향을 줄 수 있기 때문에 미리 많은 스레드를 만들어 큐에 저장 시켜 놓은 것이 쓰레드 풀이다.

    [[Java] Thread Pool(스레드 풀)](https://limkydev.tistory.com/55))
</div>
</details>


### 궁금한 점

- 다중 스레드를 단일코어에서 처리하면 무조건 동시성이고, 다중코어에서 처리하면 무조건 병렬인가??
- 46P. I/O 바운드인 동시성 알고리즘은 다중 코어, 단일코어에 상관업시 유사하다.,,?
- 코루틴 디스패처에 대한 더 자세한 개념
