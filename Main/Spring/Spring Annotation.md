

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



### @RequestMapping

클래스에 달게되면 현재 클래스의 모든 메서드들의 기본적인 URL경로를 지정하는 어노테이션

메서드에 달게되면 해당 메서드의 URL경로를 지정한다.

````java
@Controller
// 이 클래스는 /sample로 들어왔을 때 호출되게 됨
@RequestMapping("/sample/*")
@Log4j
public class SampleController {
	
	// value 값에는 URL경로, method는 전송 방식을 지정 이경우는 get post두 방식 모두 받는 메서드	
	@RequestMapping(value = "/basic", method = {RequestMethod.GET, RequestMethod.POST})
	public void basicGet() {
		log.info("basic get post");
	}
}
````



### @GetMapping, @PostMapping

RequestMapping의 축약형 Get과 Post에 대한 매핑을 나타낸다.



### @InitBinder

파라미터의 수집을 다른 용어로는 바인딩이라고 한다. 

변환이 가능한 데이터는 자동으로 변환이 되지만 파라미터를 변환하여 처리해야 하는 경우도 있다. 

> ex) 2020-11-05 같이 문자열로 된 데이터를 java.util.Date 타입으로 변환하는 작업

이때 컨트롤러에서 파라미터를 바인딩 할 때 자동으로 호출되는 어노테이션

````java
@InitBinder
	public void initBinder(WebDataBinder binder) {
		SimpleDateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd");
		binder.registerCustomEditor(Date.class, new CustomDateEditor(dateFormat, false));
	}
````



### @DateTimeFormat

파라미터로 사용되는 인스턴스 변수에 사용하여 변환하는 방식, (이 어노테이션을 사용하는 경우에는 @InitBinder는 사용하지 않는다.)

````java
@Data
public class PptaaDTO {

	private String title;
	@DateTimeFormat(pattern = "yyyy/MM/dd")
	private Date dueDate;
}
````

문자열로 'yyyy/MM/dd'의 형식이 맞다면 java.util.Date 타입으로 변환된다.



### @ModelAttribute

웹페이지의 구조는 Request에 전달된 데이터로 필요하다면 추가적인 데이터를 생성해서 화면으로 전달하는 방식으로 동작.

Model의 경우는 파라미터로 전달된 데이터는 존재하지 않지만 필요한 데이터를 전달하기 위해 사용

@ModelAttribute는 전달받은 파라미터를 강제로 Model에 담아서 전달하도록 할때 필요한 어노테이션.

파라미터로 전달된 데이터를 다시 화면에서 사용해야 할때 유용하게 사용

````java
@GetMapping("ex04")
	public String ex04(SampleDTO dto,@ModelAttribute("page") int page) {
		
		log.info("dto: "+ dto);
		log.info("page"+page);
		
		return "/sample/ex04";
	}
````





계속 추가 예정...

