### @RestController vs @Controller, 무슨 차이?

### @PostConstruct의 역할

- UserProfileController라는 Instance를 만들고 그 직후에 init 메소드를 호출하기 때문에, 해당 메서드 안에서 초기화해야 할 데이터를 초기화할 수 있다.

### PostMapping 정상적으로 안되는 에러 발생

- org.springframework.http.converter.HttpMessageNotReadableException: Required request body is missing
