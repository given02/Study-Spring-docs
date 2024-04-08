# Container Overview

org.springframework.context.ApplicationContext 인터페이스는 Spring IoC 컨테이너를 나타내며 빈의 인스턴스화, 구성 및 조립을 담당합니다. 컨테이너는 구성 메타데이터를 읽어 어떤 개체를 인스턴스화, 구성, 어셈블할지에 대한 지침을 얻습니다. 구성 메타데이터는 XML, Java Annotaion 또는 Java 코드로 표시됩니다. 이를 통해 애플리케이션을 구성하는 개체와 해당 개체 가늬 풍부한 상호 종속성을 표현할 수 있습니다.

ApplicationContext 인터페이스의 여러 구현이 Spring과 함께 제공됩니다. 독립 된 애플리케이션에서 ClassPathXmlApplicationContext 또는 FileSystemXmlApplicationContext의 인스턴스를 생성하는 것이 일반적입니다. XML은 구성 메타데이터를 정의하기 위한 전통적인 형식이었지만, 이러한 추가 메타데이터 형식에 대한 지원을 선언적으로 활성화하기 위해 소량의 XML 구성을 제공함으로써 Java Annotation 이나 코드를 메타데이터 형식으로 사용하도록 컨테이너에 지시할 수 있습니다. 

대부분의 애플리케이션 시나리오에서 명시적인 사용자 코드는 Spring IoC 컨테이너의 하나 이상의 인스턴스를 인스턴스화하는 데 필요하지 않습니다. 예를 들어, 웹 애플리케이션 시나리오에서는 일반적으로 애플리케이션의 web.xml 파일에 있는 boilerplate web descriptor XML 8줄이면 충분합니다(웹 애플리케이션을 위한 편리한 ApplicationContext 인스턴스화 참조). Eclipse용 Spring Tools(Eclipse 기반 개발 환경)를 사용하는 경우 몇 번의 마우스 클릭이나 키 입력만으로 이러한 상용구 구성을 쉽게 생성할 수 있습니다.

다음 다이어그램은 Spring이 작동하는 방식에 대한 상위 레벨에서의 측면을 보여줍니다. ApplicationContext가 생성되고 초기화된 후 완전히 구성되어 실행 가능한 시스템 또는 어플리케이션을 갖기 위해 구성 메타데이터와 결합됩니다.
