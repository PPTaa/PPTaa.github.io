# 프레젠테이션(웹) 계층의 CRUD 구현

### Controller 작성

스프링의 Controller는 하나의 클래스 내에서 여러 메서드를 작성하고 @RequestMapping등을 이용하여 URL을 분기하는 구조로 작성할 수 있기 때문에  하나의 클래스에 필요한 만큼 메서드의 분기를 이용하는 구조로 작성한다.

#### BoardController의 분석

| 작업      | URL             | Method | Parameter | From           | URL이동 |
| --------- | --------------- | ------ | --------- | -------------- | ------- |
| 전체목록  | /board/list     | GET    |           |                |         |
| 등록 처리 | /board/register | POST   | 모든 항목 | 입력 화면 필요 | 이동    |
| 조회      | /board/get      | GET    | bno = {}  |                |         |
| 삭제처리  | /board/remove   | POST   | bno       | 입력 화면 필요 | 이동    |
| 수정처리  | /board/modify   | POST   | 모든 항목 | 입력 화면 필요 | 이동    |

​	

### Controller의 처리와 테스트

웹을 개발할 때 매번 URL을 테스트 하기위해 Tomcat 과 같은 WAS를 실행하는 불편한 단계를 생략하기 위해 테스트 코드를 작성한다.

테스트 기능을 잘 활용하기만 한다면 개발 당시에 WAS를 실행하지 않고도 스프링과 웹 URL을 테스트 할 수 있다.

````java
@RunWith(SpringJUnit4ClassRunner.class)
@WebAppConfiguration //webApplicationContext라는 존재를 이용하기 위해서
@ContextConfiguration({"file:src/main/webapp/WEB-INF/spring/root-context.xml",
		"file:src/main/webapp/WEB-INF/spring/appServlet/servlet-context.xml"})
@Log4j
public class BoardControllerTests {
	@Setter(onMethod_ = {@Autowired})
	private WebApplicationContext ctx;
	
	private MockMvc mockMvc; // 가짜MVC 가짜로 URL, 파라미터 등을 브라우저에서 사용하는 것 처럼 만들어 Controller에서 실행 해 볼 수 있게 도와준다.
	
	@Before // 모든 테스트 전에 매번 실행되는 메소드
	public void setUp() {
		this.mockMvc = MockMvcBuilders.webAppContextSetup(ctx).build();
	}
	
	@Test
	public void testList() throws Exception {
		log.info(
      	//MockMvcRequestBuilders 를 통해 get방식의 호출을 함
				mockMvc.perform(MockMvcRequestBuilders.get("/board/list"))
				.andReturn()
				.getModelAndView() //Return the ModelAndView prepared by the handler.
				.getModelMap() 
      	//Model 객체를 전달하고 있다면 getModelMap()
      	//viewName을 전달한다면 getViewName()
      	//RedirectAttributes 의 flash attribute를 사용중이라면 getModelAndView() 대신 getFlashMap()을 사용할 수 있다.
				);
	}
}
````

### MVC 테스트

다음은 Spring mvc 테스트코드에서 사용 가능한 MockMvc 함수이다.

| 함수명      | 설명                                                         | 예                                                           |
| ----------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| perform     | 해당 경로로 요청하며 이때 호출할 URL과 HTTP METHOD를 설정할 수 있다 | .perform(get(”/account/1”)                                   |
| param       | 파라미터를 설정한다.                                         | .param(“key”, “value”)                                       |
| cookie      | 쿠키를 설정한다.                                             | .cookie(new Cookie(“key”, “value”)                           |
| sessionAttr | 세션을 설정한다.                                             | sessionAttr(“key”, “value”)                                  |
| accept      | response를 받을 Accept값을 설정한다.                         | .accept(MediaType.parseMediaType(“application/json;charset=UTF-8”))) |
| andExpect   | 예상값의 Assert함수                                          | andExpect(status().isOk()                                    |
| andDo       | 요청/응답에 대한 처리를 한다.                                | andDo(print())                                               |
| andReturn   | 리턴 처리한다.                                               | .andReturn()                                                 |



경우에 따라서 Controller에 test를 작성하는 것에 대해서 거부감을 가질 수 있다. 하지만 프로젝트를 진행하는 맴버들의 경험치가 낮을 수록 테스트를 먼저 진행하는 습관을 가지는 것이 좋다. 반복적인 입력과 수정, WAS의 재시작시간을 생각해보면 Controller에 대한 test를 진행하는 것이 더 빠른 개발을 할수 있는 경우가 많기 때문이다.