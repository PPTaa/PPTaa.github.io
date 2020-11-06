# Spring Naming Convention(스프링 명명규칙)

### 기본적인 네이밍 규칙

- xxxController :  스프링 MVC에서 동작하는 Controller클래스를 설계할 때 사용
- xxxService, xxxServiceImpl : 비즈니스 영역을 담당하는 인터페이스는 xxxService, 인터페이스를 구현한 클래스는 xxxServiceImpl 을 네이밍을 사용
- xxxDao, xxxRepository : DAO(Data-Access-Object)나 Repository(저장소)라는 이름으로 영역을 따로 구성하는 것이 보편적, DAO대신에 MyBatis의 Mapper 인터페이스를 활용하기도 함
- VO, DTO : VO 와 DTO는 일반적으로 유사한 의미로 사용, 데이터를 담고있는 객체를 의미한다는 공통점이 있다. VO의 경우 주로 'Read Only'의 목적이 강하며, 데이터 자체도 불변하게 설계함. DTO는 주로 데이터 수집의 목적이 강하며, 예를들명 웹 화면에서 로그인하는 정보를 DTO로 처리하는 방식을 사용한다.

### 패키지의 네이밍 규칙

기본적으로는 프로젝트의 크기나 구성원들의 성향으로 결정을 한다.

일반적으로 아래의 네이밍 규칙을 따른다.

- com.pptaa.controller : 스프링 MVC의 Controller들의 보관 패키지
- com.pptaa.config : 프로젝트와 관련된 설정 클래스들의 보관 패키지
- com.pptaa.service : 스프링의 Service 인터페이스와 구현 클래스 패키지
- com.pptaa.domain : VO, DTO 클래스들의 패키지
- com.pptaa.persistence : MyBatis Mapper 인터페이스 패키지
- com.pptaa.exception : 웹 관련 예외처리 패키지
- com.pptaa.aop : 스프링의 AOP 관련 패키지
- com.pptaa.security : 스프링의 Security 관련 패키지
- com.pptaa.util : 각종 유틸리티 클래스 관련 패키지

