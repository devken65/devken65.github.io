---
title: "Spring / Spring Annotations"
excerpt: "Spring / Spring Annotations"

categories:
  - java

tags:
  - [springboot]

toc: true
toc_sticky: true

date: 2025-05-11
last_modified_at: 2025-05-13

description: Spring / Spring Annotations 의 개념과 설명들

---
## 🔴 이 글을 쓰기 위해 참고한 영상 / 사이트 
[(블로그)Spring이란? Spring boot, Bean, 어노테이션](https://velog.io/@dmchoi224/Spring-이란-Spring-boot-Bean-어노테이션)  
[(영상)의존성 주입 3분만에 이해하기](https://youtu.be/1vdeIL2iCcM?si=e0POpzDEda7IdomP)  
[Primary, Qualifier에 대해](https://bestinu.tistory.com/58)  
[Import Annotation](https://zi-miin.tistory.com/15)  
## 🔴 Spring이란?
스프링은, 자바 기반의 웹 어플리케이션을 만들 수 있는 프레임워크이다!  
> 프레임워크란, 소프트웨어 개발을 위한 기본적인 구조 / 틀을 말한다.
> 특징으로는 재사용성, 일관성, 구조화된 개발, 확장성이 있다! 
{: .prompt-tip }
  
Python으로 따지면 Django, Ruby를 이용하는 것처럼 ( 필자는 아직 경험 중에 있음 )  
Java 개발자들은 Spring을 이용해 웹 서비스를 만들 수 있다.  
또한, Spring은 국내/외 기업에서 매우 많은 서비스를 만드는 데에 사용중에 있다. ( 특히, 자바 백엔드 개발자들은 웹 어플리케이션을 개발할 때 거의 필수라 한다 )  

### 🟠 Spring의 특징은?
Spring은 자바 객체와 라이브러리들을 관리해준다.  
Tomcat과 같은 WAS가 내장되어 있어 자바 웹 어플리케이션을 구동할 수 있다.  
> WAS : Web Application Server 의 약자이며, 웹 어플리케이션이 실행되는 환경이다!  
{: .prompt-tip }
Spring은 경량 컨테이너로 자바 객체를 직접 Spring 안에서 관리한다.
> 경량 컨테이너란, 객체의 생명주기와 의존성을 관리하는 기능을 제공하면서도, 최소한의 리소스를 사용하는 컨테이너를 말한다 
> 쉽게는, 특징중에  IOC 지원이 있는데, Spring은 IOC 컨테이너를 지원한다.
{:.prompt-tip}

Spring의 특징 중에 가장 큰 특징으로 IOC와 DI가 있다.  

#### 🟡 제어의 역전 ( IOC :  Inversion Of Control )
일반적인 자바 프로그램에서는 각 객체들이 프로그램의 흐름을 결정하며,  
사용자가 객체를 직접 생성 / 조작하는 작업을 한다. ( 사용자가 모든 작업을 제어하는 구조 )  
여기에 IOC가 적용된 경우엔,  
객체의 생성을 `특별한 관리 위임 주체`에게 맡긴다. ( 사용자가 객체를 생성하지 않고, 객체의 생명주기를 컨트롤하는 주체는 다른 주체가 된다. )  

이렇게, 사용자의 제어권을 다른 주체에 넘기는 것을 IOC( 제어의 역전 )이라 한다.  
> 클래스 내부의 객체 생성 -> 의존성 객체의 메소드 호출 ( 기존 자바 프로그램 )
> 스프링에게 제어를 위임하여 스프링이 만든 객체를 주입 -> 의존성 객체의 메소드 호출 ( IOC )
{:.prompt-tip}
#### 🟡 의존성 주입 ( DI : Dependency Injection )
여기서 의존성이란?  
```python 
class A {
  new b = new B() 
}
```
이처럼, 의존성은 하나의 코드가 다른 코드를 사용하는 것을 말한다.  
위의 경우 클래스A가 클래스B에 의존한다 라고 볼 수 있다.  ( A가 B를 사용하기에 )  

여기에 DI 개념을 넣으면, A클래스가 B클래스를 사용한다 라고 했을 때,   
A클래스에서 B클래스를 직접 생성하는 것이 아닌, 외부에서 B클래스의 인스턴스를 생성해서 주입한다 이다.  

이 외부란, 위에 나온 IOC 의 사용자가 모든 작업을 제어하는 행위가 `의존성` 이다.  
IOC는 이 제어권( 의존성 )을 특별한 관리 위임 주체(외부)에 맡긴다 했는데, 이 외부가 의존성이 있는 모듈들을 등록, 필요에 따라 스프링이 자동으로 의존하는 모듈의 생성과 해제, 주입같은 일련의 과정들을 담당하는 것이 `IOC Container`이다. 

DI 의 장점 -  
의존성 감소   
  - 변화에 강하고, 재사용성이 좋아지고, 유지보수가 용이해진다.  
  - 코드양 감소  
  - 테스트가 용이해진다. 

## 🔴 Spring Boot?
스프링을 더 쉽게 이용하기 위한 도구  
스프링을 이용하여 개발을 하게 되면 과정에서 보았듯이 세팅해야 할 요소가 많다.  
여러 세팅을 하다 보니 그만큼 진입장벽이 존재하게 되기에, Spring Boot로 매우 간단하게 프로젝트를 설정하여 개발을 더욱 용이하게 해주는 역할을 하고 있다. 

## 🔴 Spring Bean? 
Spring IOC Container 가 관리하는 자바 객체를 Bean 이라고 한다.  
기존의 자바에서는 Class를 생성해 new로 원하는 객체를 직접 생성 후 사용한다.  
Spring에서는 이 과정이 아닌, Spring에 의해 관리당하는 자바 객체를 사용한다.  

## 🔴 Annotation 정의 및 개념 
사전적의미 : 주석 ( 일반적인 주석의 의미이지만, 그 이상의 기능을 가진다. )
자바 소스 코드에 추가하여 사용할 수 있는 메타데이터의 일종이다. 
> 메타데이터는 데이터를 설명하는 데이터, 즉 데이터를 더 잘 이해하고 관리하기 위해 추가되는 정보이다. 
{:.prompt-tip}

Spring에는 여러 Annotation들이 있다.

## 🔴 Spring Core Annotations
org.springframework.beans.factory.annotation 혹은   
org.springframework.context.annotation 패키지의 주석을 사용하여 Spring DI 기능을 활용할 수 있다 

## 🔴 DI - Related Annotations
### 🟠 @Autowired 
기능 : 필요한 의존 객체의 "타입"에 해당하는 Bean을 찾아 주입한다.
사용 : 속성(field), Setter 메소드, constructor(생성자)  
이 Annotation을 사용하면, 스프링이 자동적으로 값을 할당한다.  
주로 Controller 클래스에서 DAO나 Service에 관한 객체들을 주입 시킬 때 사용한다.  

> 필드, 메소드, 생성자에 넣을 수 있고, 스프링 Bean을 가져오는 가장 기본적인 방법이다.
{:.prompt-tip}

### 🟠 @Bean 
기능 : 개발자가 직접 제어가 불가능한 외부 라이브러리 등을 Bean으로 만들려 할 때 사용한다.

### 🟠 @Primary / @Qualifier
기능 : 같은 타입의 Bean을 2개 이상 생성할 때, 하나의 Bean에게 더 높은 우선순위를 부여하기 위해 사용한다. ( 둘다 개념은 같다 )

Spring Boot 에서 어노테이션을 통해 자동으로 Bean을 컨테이너에 설정하는 경우, 같은 인터페이스의 구현체 클래스 두 개 이상이 Bean으로 등록되면 1개의 빈만 매칭되어야 한다는 에러인 `NoUniqueBeanDefinitionException`을 볼 수 있다.  
  
이 때 Spring Boot 에게 어떤 Bean을 주입할 것인지 알려줘야 하는데, 방법은 총 3가지이다.  
1. Autowired 된 field의 이름을 Bean 이름으로 설정하는 방법  
2. @Qulifier 어노테이션  
3. @Primary 어노테이션  
@Primary와 @Qulifier 에 대해 알아볼 것이니, 이 두가지만 보도록 한다.  
  
```java
public interface Animal {
  String sound();
}

// 같은 Animal을 상속받는 두 클래스 
@Component
pulbic class Dog implements Animal {
  public String sound() {
    return "왈왈";
  }
}
@Component
pulbic class Cat implements Animal {
  public String sound() {
    return "야옹";
  }
}

@Service
public class AnimalService{
  private final Animal animal;
  @Autowired
  public AnimalService(Animal animal){
    this.animal = animal; 
  }
}

// 현재 상태로 실행하면 아까 말한 오류인 NoUniqueBeanDefinitionException 이 뜬다 
// 아마 AnimalService 클래스에서의 animal이 어떤 animal인지 모호하기 때문일거다. 
```
@Qualifier 어노테이션은 Bean에 추가 구분자를 붙여주는 방법이다. 
생성자에서 해당 구분자를 명시하면, 그 구분자를 가진 Bean을 주입해주는 방식이다.  
```java
@Component
@Qualifier("dogdog")
public class Dog implements Animal {
	public String sound() {
		return "왈왈";
	}
}
@Component
@Qualifier("catcat")
public class Cat implements Animal {
	public String sound() {
		return "야옹";
	}
}

@Service
public class AnimalService {
	private final Animal animal;
	@Autowired
	public AnimalService(@Qualifier("dogdog") Animal animal) {
			this.animal = animal;
	}
}
```
> 마치 html 에서의 class나 id의 개념과 닮아있다. 
{:.prompt-tip}
  
@Primary 어노테이션은 가장 간단한 방법으로 여러 Bean이 있을 때 기본적으로 선택될 Bean을 설정하는 어노테이션이다. ( 간단히 말해 우선순위 지정 / 디폴트 Bean 지정 )  
```java
@Component
@Primary
public class Dog implements Animal {
	public String sound() {
		return "왈왈";
	}
}
@Component
public class Cat implements Animal {
	public String sound() {
		return "야옹";
	}
}

@Service
public class AnimalService {
	private final Animal animal;
	@Autowired
	public AnimalService(Animal animal) {
			this.animal = animal;
	}
}
```
>스프링은 기본적으로 자동보다 수동으로 지정한 것을 높은 우선순위를 매기기에, @Primary보다는 @Qualifier 어노테이션이 우선순위가 높다. 
{:.prompit-warning}


### 🟠 @Required
기능 : 반드시 주입해야 할 프로퍼티를 설정하는 어노테이션   
이 어노테이션이 들어간 프로퍼티는 쓰게 되면 필드 데이터는 null 이 될 수 없다.  
  
다만, Spring 5.1 이후부터는 더이상 @Required를 사용하지 않는다고 한다.  
@Required을 사용하지 않고 생성자를 이용한 주입으로 해주어야 한다.

## 🔴 Context Configuration Annotations
테스트 클래스에 적용하여 통합 테스트를 위한 로드 및 구성방법을 결정하는데 사용되는 메타데이터를 구성하는 Annotation 이다. 

### 🟠 @Import
구성(Configuration) 메타데이터를 추가하는 방법 중 하나이다.  
이를 통해 다른 구성 클래스를 로드 / 동적으로 빈을 등록 할 수 있다.  
라고는 하지만, 실은 많은 설정 클래스들이 존재할 때 하나로 합치게 도와주는 어노테이션이다. 
```java
@Configuration
@Import(ServiceConfig.class) // ServiceConfig를 포함
class AppConfig {
    @Bean
    public String appName() {
        return "MyApp";
    }
}

/*
@Configuration
class ServiceConfig {
    @Bean
    public String serviceName() {
        return "MyUserService";
    }
}
// @Import가 없다면 해당 코드를 작성하여 각각 설정해주어야 한다.
*/
```
즉, @Import 는 다른 설정 클래스를 포함해 하나의 설정으로 합치는 역할을 한다.   

### 🟠 @ImportResources
XML 설정 파일을 Spring 설정 클래스에 포함할 때 쓰인다는데.. 잘 모르겠다.

### 🟠 @PropertySource
기능 : Property 파일을 resource 폴더 내에 만들어 두고 필요할 때 해당 값을 많이 읽어옵니다. 주로 데이터베이스 연결 설정이나 Property 파일의 속성을 주입할 때 사용한다. 

Properties 파일에 app.name 으로 MySpringApp,  
app.version을 1.0.0 이라는 Property를 설정했다고 한다.  
  
```java
import org.springframework.beans.factory.annotation.Value;
import org.springframework.context.annotation.Configuration;
import org.springframework.context.annotation.PropertySource;

@Configuration
@PropertySource("classpath:config.properties") // 설정 파일 로드
public class AppConfig {
    
    @Value("${app.name}") // 값 주입
    private String appName;

    @Value("${app.version}")
    private String appVersion;

    public void printConfig() {
        System.out.println("App Name: " + appName);
        System.out.println("App Version: " + appVersion);
    }
}
```

코드와 설정을 분리 시킬 수 있는 장점이 있으며, 설정 값을 따로 관리가능하다.  
이는 중요한 정보등을 코드에 직접 노출시키지 않을 수 있다는 점이 또다른 장점으로 꼽힌다.   

## 🔴 Spring Web Annotations
### 🟠 @Controller
Spring MVC에서 컨트롤러 역할을 하는 클래스를 정의 
### 🟠 @RequestBody
클라이언트가 보낸 JSON 데이터를 객체로 반환할 때
### 🟠 @RequestMapping
웹 요청을 특정 메소드와 매핑할 때
### 🟠 @RequestParam
URL의 쿼리 파라미터를 매소드의 매개변수로 받을 때
### 🟠 @ResponseBody
컨트롤러 메소드의 반환 값을 HTTP응답(body)으로 변환할 때
### 🟠 @ExceptionHandler
예외가 발생하였을 때, 이를 처리하는 메소드를 정의할 때
### 🟠 @RestController
REST API를 위한 컨트롤러를 정의할 때  


## 🔴 Spring Boot Annotations
### 🟠 @SpringBootApplication
Spring Boot의 기본 설정을 포함하는 어노테이션 
### 🟠 @SpringBootConfiguration
Spring Boot의 설정 클래스를 정의할 때 사용하는 어노테이션
### 🟠 @EnableAutoConfiguration
Spring Boot의 자동 설정을 활성화하는 어노테이션
### 🟠 @ComponentScan
Spring에서 특정 패키지 내의 컴포넌트(Bean)을 자동으로 검색하고 등록하는 역할할

## 🔴 Spring Bean Annotations
### 🟠 @Configuration
Spring의 설정 클래스를 정의할 때 사용하는 어노테이션
### 🟠 @Component
Spring 컨테이너가 자동으로 Bean을 생성하고 관리하도록 하는 어노테이션
### 🟠 @Service
비즈니스 로직을 처리하는 서비스 계층 클래스에 붙이는 어노테이션  
주로, 서비스 역할을 하는 클래스임을 명확히 명시하기 위함이다.
### 🟠 @Repository
데이터 접근 계층(DAO)를 담당하는 클래스에 사용되는 어노테이션

## 업데이트 예정
