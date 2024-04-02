# Introduction to the Spring IoC Container and Beans

이 장에서는 Spring Fromwwork의 IoC 원칙의 구현을 다룹니다. DI(종속성 주입)는 IoC의 특수한 형식으로, 객체는 생성자 인수, 팩토리 메서드 인수 또는 팩토리 메서드에서 생성되거나 반환된 후 객체 인스턴스에 설정된 속성을 통해서만 종속성(즉, 함께 작업하는 다른 객체)을 정의합니다. 그런 다음 IoC 컨테이너는 Bean을 생성할 때 이러한 종속성을 주입합니다. 이 프로세스는 기본적으로 직접적인 클래스의 생성이나 서비스 로케이터 패턴과 같은 메커니즘을 사용하여 종속성의 인스턴스화 또는 위치를 제어하는 Bean 자체의 역(=반대, 따라서 이름이 Inversion of Control) 입니다.

org.springframework.beans 및 org.springframework.context 패키지는 Spring Framework의 IoC 컨테이너의 기초입니다. BeanFactory 인터페이스는 모든 유형의 객체를 관리할 수 있는 고급 구성 메커니즘을 제공합니다. ApplicationContext는 BeanFactory의 하위 인터페이스입니다. 이것은 다음을 추가합니다:

- Spring AOP 기능과 더 쉬운 통합
- 메시지 리소스 처리(국제화에 사용)
- 이벤트 발행
- 웹 애플리케이션에서 사용하기 위한 WebApplicationContext와 같은 애플리케이션 계층의 특정 컨텍스트

간단하게, BeanFactory는 구성 프레임워크와 기본 기능을 제공하고 ApplicationContext는 더 많은 기업특화적인 기능을 추가합니다. ApplicationContext는 BeanFactory의 완전한 상위 집합이며 이 장에서는 Spring의 IoC컨테이너 설명에 독점적으로 사용됩니다. ApplicationContext 대신 BeanFactory를 사용하는 방법에 대한 자세한 내용은 BeanFactory API를 다루는 섹션을 참조하세요.

Spring에서 애플리케이션의 핵심을 구성하고 Spring IoC 컨테이너에 의해 관리되는 객체를 Bean 이라고 합니다. Bean은 Spring IoC 컨테이너에 의해 인스턴스화, 조립 및 관리되는 객체입니다. 그밖에는 Bean은 단순히 애플리케이션의 많은 객체 중 하나일 뿐입니다. Bean과 이들 간의 종속성은 컨테이너에서 사용하는 구성 메타데이터에 반영됩니다.