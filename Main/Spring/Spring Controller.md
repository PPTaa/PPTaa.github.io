# Spring Controller

스프링 MVC 구조 가 기존의 상속과 인터페이스에서 어노테이션을 사용하는 방식으로 변한 이우헤 가장 큰 변화중 하나는 리턴타입이 자유로워 졌다는 것이다. 

### Controller의 리턴 타입

- #### String : jsp를 이용하는 경우에는 jsp파일의 경로와 파일이름을 나타내기 위해서 사용

상황에 따라 다른 화면을 보여줄 필요가 있을 때 사용(if, else...)

````java
@RequestMapping(value = "/", method = RequestMethod.GET)
public String home(Locale locale, Model model) {
  logger.info("Welcome home! The client locale is {}.", locale);

  Date date = new Date();
  DateFormat dateFormat = DateFormat.getDateTimeInstance(DateFormat.LONG, DateFormat.LONG, locale);

  String formattedDate = dateFormat.format(date);

  model.addAttribute("serverTime", formattedDate );

  return "home";
}
````

home() 메서드는 "home"이라는 문자열을 리턴했기 때문에 "/WEB-INF/views/home.jsp"경로를 리턴함.

string 앞에 redirect, forward 키워드를 붙여 리다이렉트방식과 포워드 방식을 활용 할 수 있음.

- #### void : 호출하는 URL과 동일한 이름의 jsp를 의미

````java
@GetMapping(value = "/ex")
	public void ex() {
		log.info("/ex");
	}
````

- #### VO, DTO 타입 : 주로 JSON 타입의 데이터를 만들어서 반환하는 용도로 사용

````java
@GetMapping(value = "/ex")
	public @ResponseBody SampleDTO ex() {
		log.info("/ex.....");
		SampleDTO dto = new SampleDTO();
		dto.setAge(10);
		dto.setName("Tomson");
		return dto;
	}
````

- #### ResponseEntity 타입 : response 할 때 http 헤더 정보와 내용을 가공하는 용도로 사용

````java
@GetMapping(value = "/ex")
	public ResponseEntity<String> ex() {
		log.info("/ex.....");
		String msg = "{\"name\": \"가나다\"}";
		HttpHeaders headers = new HttpHeaders();
		headers.add("Content-Type", "application/json;charset=UTF-8");
		return new ResponseEntity<>(msg, headers, HttpStatus.OK);
	}
````

ResponseEntity는 HttpHeaders 객체를 같이 전달할 수 있고, 이를 통해 원하는 HTTP 헤더 메시지를 가공하는 것이 가능

- #### Model, ModelAndView : Model 로 데이터를 반환하거나 화면까지 같이 지정하는 경우에 사용

- #### HttpHeaders : 응답에 내용없이 http헤더 메시지만 전달하는 용도



### Controller의 Exception 처리

- #### @ControllerAdvice : AOP(Aspect - Oriented - Programming)를 이용하는 방식, 공통적인 예외사항에 대해서는 별도로 @ControllerAdvice를 이용해서 분리하는 방식

````java
@ControllerAdvice // 예외처리를 목적으로 생성하는 클래스
@Log4j
public class CommonExceptionAdvice {
	
  // 해당 메서드가 ()에 들어가는 예외타입을 처리한다 
  // Exception.class를 이용했기 때문에 모든예외에 대한 처리가 except() 메소드를 통해 처리됨
  // 특정 예외에 대해 다루고 싶으면 Exception.class 대신에 구체적인 예외의 클래스를 지정해야함
	@ExceptionHandler(Exception.class) 
	public String except(Exception ex, Model model) {
	
		log.error("Exception...." + ex.getMessage());
		model.addAttribute("exception", ex);
		log.error(model);
		return "error_page";
	}
	
	@ExceptionHandler(NoHandlerFoundException.class)
	@ResponseStatus(HttpStatus.NOT_FOUND)
	public String handle404(NoHandlerFoundException ex) {
		return "custom404";
	}
}
````