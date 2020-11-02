# Spring Test Annotation

## 스프링 테스트 어노테이션에 대한 설명

### @ContextConfiguration

스프링이 실행되며 어떤 설정정보를 읽어야 하는지를 명시해준다.

locations 속성을 이용해서 xml 설정파일을 명시할 수 있다.

````java
@ContextConfiguration("file:src/main/webapp/WEB-INF/spring/root-context.xml")
````

classes 속성을 이용해서 @Configuration이 적용된 클래스를 지정해 줄 수 있다.

````java
@ContextConfiguration(classes = {RootConfig.class})
````



### @Runwith

테스트시 필요한 클래스를 지정한다. 

스프링은 SpringJUnit4ClassRunner.class 가 대상이된다.



### @Test

JUnit에서 해당 메서드가 JUnit상에서 단위테스트의 대상으로 지정해줌