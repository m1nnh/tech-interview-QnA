## Software Engineering QnA

### Q. 클린코드
A. 클린코드란 읽기 쉬운 코드가 클린코드이다. 클린코드의 가장 중요한 요소 중 하나는 가독성이라고 볼 수 있다. 즉, 모든 팀원이 이해하기 쉽도록 작성된 코드다. 가독성이 중요한 이유는 일반적으로 기존 코드를 변경하고자 할때, 해석하는 시간과 수정하는 비율이 10:1이라고 한다. 예를 들어, 코드를 변경하기 위해서 걸리는 전체 시간이 10시간이라고 하면, 사전에 코드를 분석하는 시간이 9시간 이상 걸린다는 말로 이해하면 쉽다.

### Q. SOLID
A. 클린코드 즉 설계 관점으로 클린코드를 이야기할 때 가장 많이 나오는 것이 SOLID 원칙이다. 가독성을 높이기 위해서는 SOLID 원칙을 지키며 구현해야 한다. 

S는 Simple Responsibility, 하나의 클래스는 하나의 책임만 갖는다는 원칙이며, O는 Open/Closed, 클래스는 확장에 대해 열려 있어야 하고, 변경에 대해서는 닫혀 있어야한다. L은 Liskov Substitution, 자식 클래스의 메소드는 부모 클래스의 메소드를 대체하여 사용될 수 있어야 하며, I는 Interface Segregation, 클라이언트가 사용하지 않는 메소드에 의존하면 안된다. 마지막 D는 Dependency Inversion, 추상화된 것은 구현한 것에 의존하면 안된다는 원칙이다.

즉, 네이밍이 잘되어야 하며, 오류가 없어야 한다. 중복을 피하고 의존성을 최대한 줄이며 클래스 혹은 메소드는 한 가지 일만 처리한다.

### Q. 리팩토링
A. 리팩토링이란 이미 작성한 소스코드에서 구현된 일련의 행위들을 변경없이, 코드의 가독성과 유지보수성을 높이기 위해 내부 구조를 변경하는 것이다. 다시 말해 기능을 유지하되 읽기 좋고 지속적으로 관리하기 편하게 소스코드를 재작성 하는 것이다. 리팩토링은 가독성과 유지보수성을 목표로 하며 성능을 최적화하는 것은 다른 문제다.

### Q. 클린코드와 리팩토링 차이
A. 리팩토링이 더 큰 의미를 가진 것 같다. 클린코드는 단순히 가독성을 높이기 위한 작업으로 이루어져 있다면, 리팩토링은 클린코드를 포함한 유지보수를 위한 코드 개선이 이루어진다. 클린코드와 같은 부분은 설계부터 잘 이루어져 있는 것이 중요하고, 리팩토링은 결과물이 나온 이후 수정이나 추가 작업이 진행될 때 개선해나가는 것이 올바른 방향이다.

### Q. 시큐어코딩
A. 시큐어코딩이란 안전한 소프트웨어를 개발하기 위해, 소스코드 등에 존재할 수 있는 잠재적인 보안 약점을 제거하고 보안을 고려해 기능을 설계, 구현하는 일련의 보안 활동이며 소프트웨어 개발 과정에 실행된다. 시큐어코딩 이름 그대로를 직역해보면 간단하게 알 수 있듯 안전한 코딩, 즉 보안을 위한 코딩이다. 여기에서 말하는 보안은 영화에서 나오는 것처럼 해커와 싸워 막대한 피해를 막아주는 등의 거창한 뜻을 지니고 있지만은 않다. 우리는 간혹 네이버와 같은 웹사이트에서 다른 IP로 로그인되거나 SNS 계정이 해킹당하는 경험을 한다. 조금은 사소해 보이는 상황 역시 보안이 취약해서 발생한 것이고 일상 생활에서 쉽게 접할 수 있는 일이다. 이 같은 일들을 미연에 방지하는 것이 시큐어코딩의 본질이라고 볼 수 있다.

### Q. TDD
A. TDD란 Test Driven Development의 약자로, 테스트 주도 개발을 의미한다. 즉 테스트가 개발을 이끌어 나간다고 볼 수 있다. 우리는 보통 개발할 때, 설계를 한 이후 코드 개발과 테스트 과정을 거치게 된다. 하지만 TDD는 기존 방법과는 다르게 테스트를 먼저 작성한 이후에 실제 코드를 개발하는 리팩토링 절차를 밟는다.

### Q. TDD 장단점
A. 장점은 작업과 동시에 테스트를 진행하면서 실시간으로 오류 파악이 가능하다. 짧은 개발 주기를 통해 고객의 요구사항을 빠르게 수용이 가능하며 피드백이 가능하고 진행상황 파악이 쉽다. 자동화 도구를 이용한 TDD 테스트 케이스 단위 테스트로 사용이 가능하다.

단점은 기존 개발 프로세스에 테스트 케이스 설계가 추가되므로 생산 비용이 증가한다. 테스트의 방향성, 프로젝트 성격에 따른 테스트 프레임워크 선택 등 추가로 고려할 부분이 증가한다.

### Q. TDD가 필요한 이유
A. 테스트 케이스를 작성한다는 것은 생산비용이 증가한다. 그만큼 일이 증가하는 것이기에 귀찮을 수도 있다. 실제 테스트 케이스로 확인을 안해도 결과물을 알 수 있지 않냐고 반문할 수도 있다. 하지만 실제 실무 프로젝트에서는 다양한 출력 결과물이 필요하고, 원하는 테스트 결과가 나오는지 확인하는 과정은 필수적인 부분이다. TDD를 활용하면, 처음 시작하는 단계에서 테스트 케이스를 설계하기 위한 초기 비용이 확실히 더 들지만, 개발 과정에 있어서 초기 비용보다 유지 보수비용이 더 클수 있다는 것을 명심해야 한다.

또한 안전성이 필요한 소프트웨어 프로젝트에서는 개발 초기 단계부터 확실하게 다져놓고 가는 것이 중요하다. 유지보수 비용이 더 크거나 비행기, 기차에 필요한 소프트웨어 등 안전성이 중요한 프로젝트의 경우 현재 실무에서도 TDD를 활용한 개발을 통해 이루어지고 있는 것으로 알고있다.

### Q. 애자일
A. 애자일이란 협력과 피드백을 더 자주하고, 일찍 하고, 잘하는 것이다. 애자일의 핵심은 바로 협력과 피드백이다. 애자일은 개발 과정에 있어서 시스템 변경사항을 유연하게 대응할 수 있도록 방법론을 제공해준다.
