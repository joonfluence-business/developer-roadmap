### AOP가 필요한 상황

모든 메서드의 호출 시간을 측정하고 싶다면?
시간 측정 로직을 전부 넣어라. 초 단위로 찍었는데, 밀리 세컨드로 변경해야 하는 상황이다. 이 때, 당신이라면 어떻게 해야 할까?

- try {} finally {} 구조로 적어주면 될 것임.

시간을 측정하는 로직은 공통 관심사항이다. 핵심 관심 사항은 아니다.
그렇다고 공통 로직과 핵심 로직을 함께 사용하면 유지보수가 어렵다. 변경할 때 전부 수정해야 하기 떄문임.

처음부터 나온 것은 아니고 로직 분리를 하다, AOP가 등장하게 된다.
공통 관심 사항과 핵심 관심 사항에 적용하는 것이다.
시간 측정 로직을 원하는 곳에 공통 관심 사항을 통해, 적용할 수 있다.

ProceedingJoinPoint

- joinPoint.proceed()
- @Around("execution(_ hello.hellospring._(..)")

-> 메서드에 미들웨어 만들어서 처리해주는 방식하고 비슷한 것 같다.

### 공통 관심 사항 vs 핵심 관심 사항

AOP 쓰면 된다.

### 등록방식

1) 직접 등록

- AOP 설정 여부를 확실하게 알 수 있어, 이 방식이 더 선호된다. 

```java
// SpringConfig.java

@Bean
public TimeTraceAop timeTraceAop() {
  return new TimeTraceAop();
}
```

2) 컴포넌트 스캔 방식

```java
// TimeTraceAop.java
@Aspect
@Component
public class TimeTraceAop {
  ...
}
```

### 원리

AOP 적용하면 [컨트롤러 -> Service] 에서 [컨트롤러 -> 프록시 -> Service] 로 가게 된다.
