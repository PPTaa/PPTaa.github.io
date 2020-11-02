

# Spring Annotation

## 스프링관련 어노테이션에 대한 설명

### @Component 

해당 클래스가 스프링에서 객체로 만들어서 관리하는 대상임을 명시하는 어노테이션

root-context에서 component-scan 을 통해 해당 패키지의 클래스들을 조사하며 @Component 가 존재하는 클래스들을 객체로 생성해서 빈으로 관리하게 된다.

````xml
<!-- root-context -->	
	<context:component-scan base-package="com.pptaa.sample">
	</context:component-scan>
````



### @Autowired 

스프링 내부에서 자신이 특정한 객체에 의존적이므로 자신에게 해당 타입의 빈을 주입해달라는 표시

스프링 내부에서 관리하고 있는 객체중에 이름이 맞는것을 찾아 자동으로 주입해준다.



### @Configuration

이 어노테이션을 달아 놓은 클래스는 스프링 설정을 위해 사용하는 클래스 임을 명시하는 어노테이션

스프링 프레임 워크에서는 기본 설정을 root-context.xml 파일을 이용하지만 이것 대신에 자바를 이용한 설정을 하기 위해서 어노테이션을 달아주면된다.



### @ComponentScan

java에서 설정을 적용시킬 패키지를 찾으며 해당 패키지의 클래스들을 조사해 @Component 가 존재하는 클래스들을 객체로 생성해서 빈으로 관리하게 된다.

````java
@Configuration
@ComponentScan(basePackages = {"com.pptaa.sample"})
public class RootConfig {
  ~~~~~~
}
````



### @Bean

xml 설정에서의 **\<bean\>** 태그와 동일한 역할은 한다.

 **@Bean**이 선언된 메서드의 실행 결과로 반환되는 객체는 스프링의 객체인 bean으로 등록되게 된다.



계속 추가 예정...

