## Look for Clothes QnA

### Q. Project Architecture
A. 스프링 프레임워크 경험을 쌓기 위해 리팩토링을 했다. 그래서 로컬에서 서버를 구축했다. 초기 Maven 프로젝트에서 Spring MVC와 MySQL과 자바의 관계형 데이터베이스를 프로그래밍을 좀 더 쉽게 할 수 있게 도와주는 MyBatis를 사용했다. 

### Q. MVC설정은 어떻게?
A. 원래 MVC 설정을 xml 파일로 대체하면, 클라이언트가 요청을 하게 됐을 때 DispatcherServlet이 web.xml에 등록된 내용만 가로챈다. 가로챈 요청을 HandlerMapping에 보내 해당 요청을 처리할 수 있는 Controller를 찾고 로직을 처리 후에 ViewResolver를 통해 view 화면을 찾는다. 찾은 view 화면을 view에 보내면 이 결과를 다시 DispatcherServlet에 보내고 DispatcherServlet은 클라이언트에게 전송한다.

하지만 리팩토링을 진행할 때 자바 언어로 설정 파일을 구현했다. 구현한 설정 파일은 WebAppInitializer / WebConfig / AppConfig 파일로 나누었다. WebAppInitializer 파일은 web.xml을 대체한 파일로 AbstractAnnotationConfigDispatcherServletInitializer 클래스를 상속받아 구현했다. WebConfig 파일은 DispatcherServlet 파일을 대체한 것으로 WebMvcConfigurer 인터페이스를 구현한 것이다. WebConfig 파일에서 컨트롤러 패키지를 찾고,  ViewResolver를 통해 view 화면을 찾는다. AppConfig는 ApplicationContext.xml 파일을 대체한 것으로 MyBatis와 DB 연동을 위해 사용했다.

### Q. web.xml
A. WAS가 최초 구동될 때 WEB-INF 디렉토리에 존재하는 web.xml을 읽고, 그에 해당하는 웹 애플리케이션 설정을 구성한다. 한마디로 각종 설정을 위한 설정파일이다.

### Q. Servlet
A. Servlet이란 클라이언트 요청을 처리하고, 그 결과를 반환하는 Servlet 클래스의 구현 규칙을 지킨 자바 웹프로그래밍 기술이다. 좀 더 간단히 말하면, 자바를 사용하여 웹을 만들기 위해 필요한 기술이다.

### Q. Servlet 동작방식
A. 클라이언트가 URL을 입력하면 HTTP REQUEST가 Servlet Container로 전송된다. 요청을 받은 Servlet Container는 HttpServlet Request, HttpServletResponse 객체를 생성하고, web.xml을 기반으로 사용자가 요청한 URL이 어느 서블릿에 대한 요청인지 찾는다. 해당 서블릿에서 Service 메소드를 호출한 후 클라이언트의 GET, POST 여부에 따라 doGet(), doPost()를 호출한다. 두 개의 메소드는 동적 페이지를 생성한 후 HttpServletResponse 객체에 응답을 보내고 클라이언트에게 응답한다. 응답이 끝나면 두 객체는 소멸시킨다.

### Q. Servlet Container
A. 우리가 서버에 서블릿을 만들었다고 해서 스스로 작동하는 것이 아니고, 서블릿을 관리해주는 것이 필요한데, 그러한 역할을 하는 것이 바로 Servlet Container이다. 예를 들어, 서블릿이 어떠한 역할을 수행하는 정의서라고 보면, 서블릿 컨테이너는 그 정의서를 보고 수행한다고 볼 수 있다. 서블릿 컨테이너는 클라이언트의 요청을 받아주고 응답할 수 있게, 웹서버와 소켓으로 통신하며 대표적인 예로는 톰캣이 있다. 
+ 톰캣은 실제로 웹서버와 통신하여 JSP와 Servlet이 작동하는 환경을 제공한다.

### Q. Servlet Container 역할
A. 첫 번째로, 웹서버와의 통신을 지원한다. 일반적으로 우리는 소켓을 만들고 listen, accept 등을 해야하지만 서블릿 컨테이너는 이러한 기능을 API로 제공하여 복잡한 과정을 생략할 수 있게 해준다. 그래서 개발자가 서블릿에 구현해야 할 비지니스 로직에 대해서만 초점을 두게끔 도와준다.
두 번째로, Servlet Life Cycle을 관리해준다. 서블릿 클래스를 로딩하여 인스턴스화하고, 초기화 메소드를 호출하고, 요청이 들어오면 적절한 서블릿 메소드를 호출한다. 또한 서블릿이 생명을 다 한 순간에는 적정하게 Garbage Collection을 진행하여 편의를 제공한다.
세 번째로, 멀티쓰레드 지원 및 관리한다. 요청이 올 때마다 새로운 자바 쓰레드를 하나 생성하는데, HTTP 메소드를 실행하고 나면, 쓰레드는 자동으로 죽게된다. 원래는 쓰레드를 관리해야 하지만 서버가 다중 쓰레드를 생성 및 운영해주니 쓰레드의 안정성에 대해서는 걱정하지 않아도 된다.
마지막으로 보안 관리가 가능하다. 서블릿 컨테이너를 사용하면 개발자는 보안에 관련된 내용을 서블릿 또는 자바 클래스에 구현해 놓지 않아도된다. 일반적으로 보안관리는 XML 배포 서술자에다가 기록하므로, 보안에 대해 수정할 일이 생겨도 자바 소스 코드를 수정하여 다시 컴파일하지 않아도 보안관리가 가능하다.

### Q. Servlet Life Cycle
A. 클라이언트의 요청이 들어오면 컨테이너는 해당 서블릿이 메모리에 있는지 확인하고, 없을 경우 init() 메소드를 호출하여 메모리에 적재한다. init() 메소드는 처음 한번만 실행되기 때문에, 서블릿의 쓰레드에서 공통적으로 사용해야하는 것이 있다면 오버라이딩하여 구현하면 된다. 실행 중 서블릿이 변경될 경우, 기존 서블릿을 파괴하고 init()을 통해 새로운 내용을 다시 메모리에 적재한다.
init()이 호출된 후 클라이언트의 요청에 따라서 Service() 메소드를 통해 요청에 대한 응답이 doGet(), doPost()로 분기된다. 이때 서블릿 컨테이너가 클라이언트의 요청이 오면 가장 먼저 처리하는 과정으로 생성된 HttpServletRequest, HttpServletResponse에 의해 request와 response 객체가 제공된다.
컨테이너가 서블릿에 종료 요청을 하면 destroy() 메소드가 호출되는데 마찬가지로 한번만 실행되며, 종료시에 처리해야하는 작업들은 destroy() 메소드를 오버라이딩하여 구현하면 된다.

### Q. MyBatis
A. 자바의 관계형 데이터베이스 프로그래밍을 좀 더 쉽게 할 수 있게 도와주는 개발 프레임워크로써 JDBC를 통해 데이터베이스에 액세스 하는 작업을 캡슐화하고 일반 SQL 쿼리, 저장 프로시저 및 고급 매핑을 지원하며 모든 JDBC 코드 및 매개 변수의 중복 작업을 제거한다. Mybatis에서는 프로그램에 있는 SQL 쿼리들을 한 파일에 구성하여 프로그램 코드와 SQL을 분리할 수 있는 장점을 가지고 있다.

### Q. MyBatis 특징
A. 복잡한 쿼리나 다이나믹한 쿼리에 강하며, 프로그램 코드와 SQL 쿼리의 분리로 코드의 간결함 및 유지 보수성이 향상된다. 빠른 개발이 가능하여 생산성이 향상되기도 한다.

### Q. 실행 순서
A. 클라이언트가 URL을 요청하면, 웹 브라우저에서 스프링으로 Request가 보내진다. 이때 Dispatcher Servlet이 Request를 받으면 Handler Mapping을 통해 해당 URL을 담당하는 Controller를 탐색 후 찾아낸다. 찾아낸 Controller로 Reqeust를 보내주고, 보내주기 위해 필요한 Model을 구성한다. Model에서는 페이지 처리에 필요한 정보들을 Database에 접근하여 쿼리문을 통해 가져온다. 데이터를 통해 얻은 Model 정보를 Controller에게 response 해주면, Controller는 이를 받아 Model을 완성시켜 Dispatcher Servlet에게 전달하고, Dispatcher Servlet은 view Resolver를 통해 request에 해당하는 view 파일을 탐색 후 받아낸다. 받아낸 View 페이지 파일에 Model을 보낸 후 클라이언트에게 보낼 페이지를 완성시켜 받아낸 후, 완성된 view 파일을 클라이언트에게 response하여 화면에 출력한다.

### Q. DAO / DTO / VO
A. DAO는 Data Access Object의 약자로 데이터베이스의 데이터에 접근하기 위한 객체이다. 데이터베이스 접근을 하기 위한 로직과 비지니스 로직을 분리하기 위해 사용한다. DAO의 경우 데이터베이스와 연결할 Connection까지 설정되어 있는 경우가 많다. 그래서 현재 많이 쓰이는 MyBatis 등을 사용할 경우 커넥션풀까지 제공되고 있기 때문에 별도로 만드는 경우는 드물다.
DTO는 Data Transfer Object의 약자로 계층간 데이터 교환을 위한 자바 Beans를 의미한다. DTO는 로직을 가지지 않는 순수한 데이터 객체이고 getter, setter 메소드만을 가진 클래스를 의미한다.
VO는 Value Object의 약자로 값 오브젝트로써 값을 위해 쓰인다. 자바는 값 타입을 표현하기 위해 불변 클래스를 만들어서 사용한다. 이런 클래스는 중간에 바꿀 수 없고 새로 만들어야 한다는 특징이 있다.
DTO와 VO의 공통점은 넣어진 데이터를 getter를 통해 사용하므로 주 목적은 같지만, DTO의 경우는 가변의 성격을 가진 클래스이다. 그에반해 VO는 불변의 성격을 가진 차이점이 있다.

### Q. 옷찾사 프로젝트
A. ‘옷을 찾아주는 사람들’이라는 주제로 졸업작품 프로젝트를 수행했다. 오프라인 매장 이용 활성화를 위해 매장별 옷의 정보, 재고에 대한 데이터베이스를 구축하여 원하는 옷의 재고가 없을 때 가까운 매장을 찾아주는 서비스이다. 코로나가 터지기 전에, 실제 학생들을 대상으로 온라인 설문조사를 통해서 아직까지 온라인 쇼핑보다 오프라인 쇼핑의 선호도가 더 높아서 진행했었다.

### Q. 그때 당시의 서버 구성
A. 그때도 서버를 맡았었다. 하지만 처음 다루는 것이다 보니 무거운 프레임워크를 사용하는 것보다 가벼운 것을 사용했다. 그래서 APM을 통해 개발을 했다.

### Q. Spring Triangle
A. IOC는 Inversion of Control의 약자로 제어의 역전이다. 스프링에서는 제어권이 컨테이너가 관리하면서 객체의 생성 및 생명주기를 관리한다. DI는 Dependency Injection의 약자로 의존성 주입이다. 의존성이란, 어떠한 작업1을 변경 하기 위해 다른 작업2까지 변경해야 하는 경우 작업1이 작업2에 대해 의존성을 가지고 있다고 한다. 이 의존성을 해결 하기 위해 객체의 인스턴스를 외부에서 받을 필요가 있다.(setter) AOP는 Aspect Oriented Programming의 약자로 관점 기준으로 각각을 모듈화 하는 관점지향 프로그래밍으로 객체지향을 더 객체지향으로 사용할 수 있게 한다. 공통적인 기능을 AOP에 정의해서 한 기능을 수행 할 때 이 기능을 수행하기 전에 수행을 하게 설정하거나 기능 후에 실행하게 끔 설정을 하여 쓰는 것이다. (트랜잭션, 보안, 권한)

### Q. 왜 리팩토링?
A. 회사에서는 멀티쓰레드 기반의 스프링 프레임워크를 선호한다. 그 이유는 아마 대용량 트래픽을 처리하는 데 있어서 유리해서 그런 것 같다. 그래서 취업하기까지 시간이 얼마 남지 않았기 때문에, 새로운 프로젝트를 진행하는 것은 무리가 있었고, 자바 언어에 대해 조금 익숙해지려고 리팩토링을 진행했다.

### Q. 어려웠던 점
A. 애초에 API를 목적으로 리팩토링을 한 것이 아니라, 스프링을 경험해 보고 싶어 진행했다. 그래서 초기 환경설정과, 익숙하지 않은 언어를 사용하는 것이 어려웠다. ~등등등