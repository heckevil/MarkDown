#  스프링

- 스프링 프레임 워크는 약 20개의 모듈로 구성되어 있다.
- 필요한 모듈만 가져다가 사용할 수있다.





##  컨테이너

- 컨테이너 는 인스턴스의 생명주기를 관리한다.(life Cycle)
- 생성된 인스턴스들에게 추가적인 기능을 제공한다



## IOC

- imversion of Control 
- 개발자는 프로그램의 흐름을 제어하는 코드를 작성한다.

그런데, 이 흐름의 제어를 개발자가 하는 것이 아니라 다른 프로그램이 그 흐름을 제어하는 것을 ioc라고 한다.



## DI

- Dependency injection , 의존성 주입
- DI는 클래스 사이 의존관계를 빈 설정을 바탕으로 컨테이너가 자동으로 연결해주는 것을 말한다.

EX)

```java
//di 적용 X

class 엔진 {}
class 자동차 {
 	엔진 v5 = new 엔진()

}

//di 적용O

@Component
class 엔진{}

@Component
class 자동차{
	@Autowired
	엔진v5;

}

```



## IoC/Di컨테이너

- BeanFactiory : 기본적인 기능
- Application Context : BeanFactiory 모든 기능 포함 보다더 다양한 기능을 가지고 있음 .