

# Spring Annotation

## 스프링관련 어노테이션에 대한 설명

### @Component 

해당 클래스가 스프링에서 객체로 만들어서 관리하는 대상임을 명시하는 어노테이션

root-context에서 component-scan 을 통해 해당 패키지의 클래스를 조사하며 @Component 가 존재하는 클래스들을 객체로 생성해서 빈으로 관리하게 된다.

````xml
<!-- root-context -->	
	<context:component-scan base-package="com.pptaa.sample">
	</context:component-scan>
````



### @Autowired 

스프링 내부에서 자신이 특정한 객체에 의존적이므로 자신에게 해당 타입의 빈을 주입해달라는 표시

스프링내부에서 관리하고 있는 객체중에 이름이 맞는것을 찾아 자동으로 주입해준다.



계속 추가 예정...

