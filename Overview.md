# Overview

Spring을 사용하며 Java 엔터프라이즈 애플리케이션을 쉽게 만들 수 있습니다. JVM의 대체 언어로 Groovy 및 Kotlin을 지원하고 애플리케이션 요구 사항에 따라 다양한 종류의 아키텍처를 생성할 수 있는 유연성을 통해 엔터프라이즈 환경에서 Java언어를 수용하는 데 필요한 모든 것을 제공합니다. Spring Framework 6.0부터 Spring에는 Java 17 이상이 필요합니다.

Spring은 광범위한 애플리케이션 시나리오를 지원합니다. 대기업에서는 애플리케이션이 오랫동안 존재하고 업그레이드 주기가 개발자의 통제 범위를 벗어나는 JDK 및 애플리케이션 서버에서 실행되어야 하는 경우가 많습니다. 다른 것들은 클라우드 환경에서 서버가 내장된 단일 jar로 실행될 수 있습니다. 그러나 다른 것들은 서버가 필요하지 않은 독립 실행형 애플리케이션(예: 배치 또는 통합 워크로드)일 수 있습니다.

스프링은 오픈소스 입니다. 다양한 실제 사용사례를 기반으로 지속적인 피드백을 제공하는 크고 활동적인 커뮤니티가 있습니다. 이는 Spring이 오랜 시간 동안 성공적으로 발전하는 데 도움이 되었습니다.

# What We Mean by "Spring"

"Spring"이라는 용어는 상황에 따라 다른 것을 의미합니다. 이는 모든 것이 시작된 Spring Framework 프로젝트 자체를 말하는 데 사용될 수 있습니다. 시간이 지나서는 다른 Spring 프로젝트가 Spring Framework 기반으로 구축되었습니다. 대부분 사람들이 "Spring"이라고 하면 전체 프로젝트를 의미합니다. 이 참조 문서는 Spring Framework 자체의 기초에 중점을 둡니다.

Spring Framework는 모듈로 나누어져 있습니다. 애플리케이션은 필요한 모듈을 선택할 수 있습니다. 그 중심에는 구성 모델(configuration model)과 종속성주입 메커니즘(dependency injection mechanism)을 포함하는 코어 컨테이너 모듈이 있습니다. 그 외에도 Spring Framework는 메시징, 트랜잭션 데이터 및 지속성, 웹을 포함한 다양한 애플리케이션 아키텍처에 대한 기본 지원을 제공합니다. 또한 Servlet 기반 Spring MVC 웹 프레임워크와 동시에 Spring WebFlux 반응형 웹 프레임워크도 포함되어 있습니다.

모듈에 대한 참고사항 : Spring의 프레임워크 jar를 사용하면 JDK 9의 모듈 경로("Jigsaw")에 배포할 수 있습니다. Jigsaw 지원 애플리케이션에서 사용하기 위해 Spring Framework 5 jar에는 다음과 독립적으로 안정적인 언어 수준 모듈 이름("spring core", "spring.context" 등)을 정의하는 "Automatic-Module-Name" 매니페스트 항목이 함께 제공됩니다. jar 아티팩트 이름(jar는 "."대신 "-"를 사용하여 동일한 명명 패턴을 따릅니다(예: "spring-core" 및 "spring-core" 및 "spring-context")). 물론 Spring의 프레임워크 jar는 JDK8과 9+의 클래스 경로에서 잘 작동합니다.

# History of Spring and the Spring Framework

Spring은 초기 J2EE 사양의 복잡성에 대한 대응으로 2003년에 등장했습니다. 일부에서는 Java EE와 최신 후속 버전인 Jakarta EE가 Spring과 경쟁 광계에 있다고 생각하지만 실제로는 상호 보완적입니다. Spring 프로그래밍 모델은 Jakarta EE 플랫폼 사양을 수용하지 않습니다. 오히려 전통적인 EE 우산에서 엄선된 개별 사양과 통합됩니다.

- Servlet API (JSR 340)
- WebSocket API (JSR 356)
- Concurrency Utilities (JSR 236)
- JSON Binding API (JSR 367)
- Bean Validation (JSR 303)
- JPA (JSR 338)
- JMS (JSR 914)
- as well as JTA/JCA setups for transaction coordination, if necessary.

Spring Framework는 애플리케이션 개발자가 Spring Framework에서 제공하는 Spring 특정 메커니즘 대신 사용하도록 선택할 수 있는 Dependency Injection(JSR 330) 및 Common Annotations(JSR 250) 사양도 지원합니다. 근본적으로 일반적인 javax 패키지를 기반으로 했습니다.

Spring Framework 6.0부터 Spring은 전통적인 javax 패키지 대신 jakarta 네임스페이스를 기반으로 Jakarta EE 9레벨(예: Servlet 5.0+, JPA 3.0+)로 업그레이드 되었습니다. 최소 EE 9와 이미 지원되는 EE 10을 통해 Spring은 Jakarta EE API의 추가 발전을 위한 기본 지원을 제공할 준비가 되어 있습니다. Spring Framework 6.0은 웹 서버인 Tomcat 10.1, Jetty 11 및 Undertow 2.3 및 Hibernate ORM 6.1과 완벽하게 호환됩니다.

시간이 지남에 따라 애플리케이션 개발에서 Java/Jakarta EE의 역할이 발전했습니다. J2EE 및 Spring 초기에는 애플리케이션이 애플리케이션 서버에 배포되기 위해 만들어졌습니다. 오늘날에는 Spring Boot의 도움으로 애플리케이션은 DevOps 및 클라우드 친화적인 방식으로 생성되며 서블릿 컨테이너가 내장되어 있어 변경이 쉽습니다. Spring Framework 5부터 WebFlux 애플리케이션은 Servlet API를 직접 사용하지 않고 Servlet 컨테이너가 아닌 서버(예: Netty)에서 실행될 수 있습니다.

Spring은 계속해서 혁신하고 진화하고 있습니다. Spring Framework 외에도 Spring Boot, Spring Security Spring Data, Spring Cloud, Spring Batch 등과 같은 다른 프로젝트가 있습니다. 각 프로젝트에는 자체 소스 코드 저장소, 이슈 추적기 및 릴리스 흐름이 있다는 점을 기억하는 것이 중요합니다. Spring 프로젝트의 전체 목록은 spring.io/projects를 참조하세요.

# Design Philosophy

프레임워크에 대해 배울 때 프레임워크가 수행하는 작업뿐만 아니라 따르는 원칙도 아는 것이 중요합니다. Spring Framework의 기본 원칙은 다음과 같습니다.

- 모든 수준에서 선택권 제공. Spring을 사용하면 디자인 결정을 가능한 늦게 연기할 수 있습니다. 예를 들어, 코드를 변경하지 않고도 구성을 통해 지속성 공급자를 전환할 수 있습니다. 다른 많은 인프라 문제 및 타사 API와의 통합에서도 마찬가지 입니다.

- 다양한 관점 수용. Spring은 유연성을 수용하며 작업 수행 방법에 대해 고집을 부리지 않습니다. 다양한 관점으로 광범위한 애플리케이션 요구 사항을 지원합니다.

- 강력한 이전 버전과의 호환성 유지. Spring의 발전은 버전 간 주요 변경 사항을 거의 강제하지 않도록 신중하게 관리되었습니다. Spring은 Spring에 의존하는 애플리케이션과 라이브러리의 유지 관리를 용이하게 하기 위해 신중하게 선택된 다양한 JDK 버전과 타사 라이브러리를 지원합니다.

- API 디자인 중시. Spring 팀은 직관적이고 여러 버전과 수년에 걸쳐 유지되는 API를 만들기 위해 많은 생각과 시간을 투자합니다.

- 코드 품질에 대한 높은 기준 설정. Spring Framework는 의미 있고 최신이며 정확한 javadoc에 중점을 둡니다. 패키지 간 순환 종속성(circular dependencies)이 없는 깔끔한 코드 구조를 주장할 수 있는 몇 안 되는 프로젝트 중 하나입니다.

# Feedback and Contributions

For how-to questions or diagnosing or debugging issues, we suggest using Stack Overflow. Click here for a list of the suggested tags to use on Stack Overflow. If you’re fairly certain that there is a problem in the Spring Framework or would like to suggest a feature, please use the GitHub Issues.

If you have a solution in mind or a suggested fix, you can submit a pull request on Github. However, please keep in mind that, for all but the most trivial issues, we expect a ticket to be filed in the issue tracker, where discussions take place and leave a record for future reference.

For more details see the guidelines at the CONTRIBUTING, top-level project page.

# Getting Started

If you are just getting started with Spring, you may want to begin using the Spring Framework by creating a Spring Boot-based application. Spring Boot provides a quick (and opinionated) way to create a production-ready Spring-based application. It is based on the Spring Framework, favors convention over configuration, and is designed to get you up and running as quickly as possible.

You can use start.spring.io to generate a basic project or follow one of the "Getting Started" guides, such as Getting Started Building a RESTful Web Service. As well as being easier to digest, these guides are very task focused, and most of them are based on Spring Boot. They also cover other projects from the Spring portfolio that you might want to consider when solving a particular problem.
