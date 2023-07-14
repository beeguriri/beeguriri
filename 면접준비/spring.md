### 💜 스프링이란?
- 자바의 오픈소스 애플리케이션 프레임워크 중 하나로
- 특정 기술에 종속 되지 않고
- 객체를 관리할 수 있는 프레임워크를 제공
- 컨테이너로 자바 객체를 관리하면서 의존성 주입과 제어의 역전을 통해 결합도를 낮춤

#### 🎈 스프링 빈의 라이프사이클
- 스프링 IoC 컨테이너 생성 → 스프링 빈 생성 → 의존관계 주입 → 초기화 콜백 메소드 호출 → 사용 → 소멸 전 콜백 메소드 호출 → 스프링 종료

#### 🎈  IoC(Inversion of Controller)
- 제어의 역전 : 제어권이 사용자에게 있지 않고, 프레임워크에 있음
    - 제어권이 객체(클라이언트 코드)에 있는 것이 아니라, AppConfig에서 가지고 있음
- 프레임워크가 전체의 흐름을 정해놓고
- 필요에 따라 개발자(사용자)의 코드를 호출
- 스프링에서 인스턴스의 생성부터 소멸까지 컨테이너에서 대신 관리
  
#### 🎈 스프링 빈 생성
- `@Component` 어노테이션을 통한 자동 생성 (`@Controller`, `@Service`, `@Repository` 포함)
- `@Configuration`과 `@Bean`을 통한 생성

#### 🎈 DI(Dependency Injection)
- 의존성 주입, 컨테이너가 의존관계를 자동으로 연결
- 직접 의존하는 객체를 생성하거나 검색해서 가져올 필요가 없어 결합도가 낮아지는 장점이 있음
- 애플리케이션 실행시점(런타임)에 외부에서 실제 구현 객체를 생성하고 클라이언트에 전달해서 
- 클라이언트와 서버의 실제 의존 관계가 연결 되는 것 (`@Configuration` 클래스 이용)
- 클라이언트 코드를 변경하지 않고, 클라이언트가 호출하는 대상의 타입 인스턴스 변경 가능
  
#### 🎈 생성자 주입
- 생성자의 호출 시점에 1회 호출 되는 것이 보장
- 주입받은 객체가 변하지 않거나, 반드시 객체의 주입이 필요한 경우 사용
- final 키워드와 `@RequiredArgsConstructor` 어노테이션을 사용해 컴파일 시점에 객체를 주입받아 사용

#### 🎈 초기화 콜백 메소드 호출, 소멸 전 콜백 메소드 호출
- `@PostConstruct`, `@PreDestory` 어노테이션 사용

#### 🎈 Spring의 싱글톤 패턴
- 스프링에서 bean 생성시 별다른 설정이 없으면 default로 싱글톤 적용
- 스프링은 컨테이너를 통해 직접 싱글톤 객체를 생성하고 관리하는데,
- 요청이 들어올 때마다 매번 객체를 생성하지 않고, 이미 만들어진 객체를 공유하기 때문에 효율적인 사용이 가능

### 💜 AOP란?
- 관점지향 프로그래밍: Aspect Oriented Programming
- 트랜잭션이나 로깅, 보안(인증)과 같이 여러 모듈에서 공통적으로 사용하는 기능을 분리

### 💜 스프링과 스프링 부트 차이
- Auto Configuration
- Spring Boot는 설정의 많은 부분을 자동화
- spring boot starter dependency만 추가해주면 설정은 끝나고, 내장된 톰캣을 제공해 서버를 바로 실행할 수 있음

### 💜 스프링 MVC
- Model, View, Controller의 약자이며, 각 레이어간 기능을 구분하는데 중점을 둔 디자인 패턴
- Model: 데이터 관리 및 비즈니스 로직을 처리하는 부분 (DAO, DTO, Service 등)
- View: 비즈니스 로직의 처리 결과를 통해 유저 인터페이스 표현 (html, jsp, tymeleaf 등을 이용한 화면 구성 또는 json 응답으로 구성)
- Controller: 사용자의 요청을 처리하고 Model과 View를 중개하는 역할
 
#### 🎈 MVC 요청 처리 흐름
<img src="https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FwQtNl%2Fbtru2nkxWie%2FsUL4eKBFf4BRQFs1JE7ijK%2Fimg.png"> 
- 1. 클라이언트는 URL을 통해 요청을 전송한다.
- 2. 디스패처 서블릿은 핸들러 매핑을 통해 해당 요청이 어느 컨트롤러에게 온 요청인지 찾는다.
- 3. 디스패처 서블릿은 핸들러 어댑터에게 요청의 전달을 맡긴다.
- 4. 핸들러 어댑터는 해당 컨트롤러에 요청을 전달한다.
- 5. 컨트롤러는 비즈니스 로직을 처리한 후에 반환할 뷰의 이름을 반환한다.
- 6. 디스패처 서블릿은 뷰 리졸버를 통해 반환할 뷰를 찾는다.
- 7. 디스패처 서블릿은 컨트롤러에서 뷰에 전달할 데이터를 추가하고
- 8. 데이터가 추가된 뷰를 반환한다.

#### 🎈 디스패처 서블릿이란?
- DispatcherServlet : 클라이언트에게 요청을 받아 응답까지의 MVC 처리과정을 통제한다.
- HandlerMapping : 클라이언트의 요청 URL을 어떤 Controller가 처리할지 결정한다.
- HandlerAdapter : HandlerMapping에서 결정된 핸들러 정보로 해당 메소드를 직접 호출해주는 역할을 한다.
- ViewResolver : Controller의 처리 결과(데이터)를 생성할 view를 결정한다.

### 💜 [필터와 인터셉터 차이](https://dev-coco.tistory.com/173)
- 클라이언트 > `필터` > 디스패처 서블릿 > `인터셉터` > 컨트롤러

#### 🎈 필터
- 스프링 컨테이너가 아닌 톰캣과 같은 웹 컨테이너에 의해 관리
- Dispatcher Servlet에 요청이 전달되기 전 / 후에 url 패턴에 맞는 모든 요청에 대해 부가 작업을 처리할 수 있는 기능을 제공
- 적용 예:
  - 보안 및 인증/인가 관련 작업
  - 모든 요청에 대한 로깅 또는 검사
  - 이미지/데이터 압축 및 문자열 인코딩
  - Spring과 분리되어야 하는 기능

#### 🎈 인터셉터
- 웹 컨테이너에서 동작하는 필터와 달리 인터셉터는 스프링 컨텍스트에서 동작
- Dispatcher Servlet이 Controller를 호출하기 전/후에 인터셉터가 끼어들어 요청과 응답을 참조하거나 가공할 수 있는 기능을 제공
- 인터셉터가 없다면 바로 컨트롤러를 실행
- 적용 예:
- 세부적인 보안 및 인증/인가 공통 작업
- API 호출에 대한 로깅 또는 검사
- Controller로 넘겨주는 정보(데이터)의 가공
 
### 💜 @RequestBody, @RequestParam, @ModelAttribute의 차이
- `@RequestBody`: 클라이언트가 전송하는 JSON 형태의 HTTP Body 내용을 MessageConverter를 통해 Java Object로 변환
- `@RequestParam`:  HTTP 요청 파라미터(데이터)를 받기 위해 사용(uri?RequestParam1,2,3,..)
  - default required가 true이므로 반드시 해당 파라미터가 전송되어야 함.
- `@PathVariable`:  HTTP 요청 파라미터(데이터)를 받기 위해 사용(uri/{pathVariable}, 값을 하나만 받아올 수 있음.
- `@ModelAttribute`: HTTP Body 내용과 HTTP 파라미터의 값들을 생성자,Getter,Setter를 통해 주입하기 위해 사용

### 💜 Lombok 라이브러리
- 메서드를 컴파일 하는 과정에 개입해서 추가적인 코드를 만들어냄 (어노테이션 프로세싱)
  - 어노테이션 프로세싱: 자바 컴파일러가 컴파일 단계에서 어노테이션을 분석하고 처리하는 기법

<hr>

### 💜 ORM (Object Relation Mapping)
- 관계형 데이터베이스(RDBMS)를 객체지향프로그래밍언어(OOP)로 변환해 주는 기술
- 객체와 테이블을 Mapping하여
- 비즈니스 코드가 테이블에 접근할 수 있도록 함

### 💜 JPA (인터페이스)
- ORM을 위해 자바에서 제공하는 API
- 자바 객체와 DB 테이블을 Mapping하며
- 대표적인 구현체로 Hibernate가 있음.
  
### 💜 ORM, JPA, Hibernate 장단점
- 비즈니스 로직에 집중할 수 있음
- 테이블을 객체로 만들기 떄문에 객체중심의 개발 가능
- 메서드 호출로 쿼리를 수행해서 생산성 향상, 유지보수 비용 감소
- 특정 DB에 의존하지 않음 (DB마다 쿼리 변환을 해줄 필요가 없음)
- 복잡한 쿼리는 메서드로 처리가 힘들다는 단점이 있음.

### 💜 JPA N + 1 문제
- 1번의 쿼리를 날렸을 때 의도하지 않은 N번의 쿼리가 추가적으로 실행
- xToOne 맵핑 시 Fetch 전략이 EAGER 전략으로 데이터를 조회하는 경우
- JPA Fetch 전략이 LAZY 전략으로 데이터를 가져온 이후에 연관 관계인 하위 엔티티를 다시 조회하는 경우
- Fetch Join을 사용해 해결 (미리 두 테이블을 Join하여 한 번에 모든 데이터를 가져오기)

### 💜 [Transaction](https://mangkyu.tistory.com/30)
- 스프링에서 클래스나 메서드에 `@Transactional` 어노테이션을 붙여 사용
- 해당 메서드 실행 중 RuntimeException이 발생하면 트랜잭션이 롤백 됨
- `@Transactional(read=only)`: 해당 트랜잭션을 읽기전용으로 하는 경우 사용
- **AOP 관련 공부 더 해야겠다...**

#### 🎈 트랜잭션 
- DBMS에서 데이터를 다루는 논리적인 작업의 단위
- DB에서 데이터를 다룰 때 장애가 일어난 경우 데이터를 복구하는 작업의 단위가 된다.
- DB에서 여러 작업이 동시에 같은 데이터를 다룰 때가 이 작업을 서로 분리하는 단위가 된다.
- 트랜잭션은 전체가 수행되거나 또는 전혀 수행되지 않아야 한다.

#### 🎈 트랜잭션 ACID
- 원자성(Atomicity): 트랜잭션에 포함된 작업은 전부 수행되거나 전부 수행되지 않아야 한다.
- 일관성(Consistency): 트랜잭션을 수행하기 전이나 후나 데이터베이스는 항상 일관된 상태를 유지해야 한다.
- 고립성(Isolation): 수행 중인 트랜잭션에 다른 트랜잭션이 끼어들어 변경중인 데이터 값을 훼손하지 않아야한다.
- 지속성(Durability): 수행을 성공적으로 완료한 트랜잭션은 변경한 데이터를 영구히 저장해야 한다.

### 💜 DTO, VO 그리고 Entity?
- Entity: 실제 DataBase의 테이블과 1 : 1로 매핑되는 클래스
- DTO (Data Transfer Object): 데이터 전송(이동) 객체, getter/setter 메소드 가짐
- Entity와 DTO를 분리하는 이유: DB 와 View 사이의 역할 분리
- VO (Value Object): VO는 변하지 않는 데이터 객체, getter만 가능(read만 가능)
- DTO와 VO의 차이: DTO는 데이터 전달만을 목적으로 하고, VO는 객체 자체를 어떠한 값(Value)으로서 사용
  - 외부 시스템과 데이터 통신을 할 경우 DTO로, DB에서 가져오는 Data는 VO로 정의 후 사용

#### 🎈 참조블로그
- [Lea Hwang](https://lealea.tistory.com/224)
- [coco3o](https://dev-coco.tistory.com/163)
