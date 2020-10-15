## Spring Batch

스프링 배치는 스프링의 특성을 그대로 가지고 있는 것으로서, 스프링의 3대 요소인 **DI, AOP, 추상화** 를 모두 사용할 수 있다.

---

## Spring Batch 프로젝트 생성

![image](https://user-images.githubusercontent.com/40616436/95339617-35568280-08ef-11eb-8a9e-ae5d743dffa2.png)

![image](https://user-images.githubusercontent.com/40616436/95339879-84041c80-08ef-11eb-8d58-77b157426f3b.png)

---

## Spring Batch Job

Spring Batch에서 job이란  batch에 시작 단계이며, job 안에서 모든 step들을 구성할 수 있다.

먼저, 생성한 repository에서 main이 선언되어 있는 demoApplication을 열어보면 Application을 실행할 수 있는 최소한의 코드가 구성되어 있다.

<img src="https://user-images.githubusercontent.com/40616436/95341359-2244b200-08f1-11eb-9bf1-4b8568d1b04a.png" alt="image" style="zoom:50%;" />

그리고 **해당 클래스에서 Spring Batch 기능을 사용하기 위한 어노테이션인 *@EnableBatchProcessing* 을 추가해야 한다.**

