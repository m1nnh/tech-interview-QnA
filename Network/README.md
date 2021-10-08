## Network QnA

### Q. 웹 통신의 큰흐름
A. 사용자가 URL을 입력해서 엔터 치면 DNS 서버에서 해당 URL에 매핑되는 IP 값을 찾아온다. 해당 IP 주소로 HTTP 요청 메시지를 보내고, 서버는 그에 해당하는 응답 메시지를 반환해 HTML 렌더링을 통해 화면에 출력한다.

### Q. URI / URL / URN
A. URI는 네트워크 상에 있는 자원을 가리키는 식별자이다. URL과 URN은 URI라는 큰 범주 안에 포함되는데, URL은 해당 자원의 path, 즉 위치를 알려주고, URN은 자원의 이름으로 프로토콜을 제외한 부분이다.

### Q. 프로토콜
A. 컴퓨터와 컴퓨터가 통신할 때도 지켜야할 절차나 규약을 프로토콜이라 한다. 대표적인 프로토콜에는 http, https, ftp, sftp가 있다.

### Q. 포트포워딩
A. 클라이언트와 서버를 분리해 외부에서 서버로 접속을 가능하게 하는 기술이 포트포워딩이다. 예를 들어, 공유기를 사용한다 치면, 그 공유기는 고정 IP 주소를 할당받게 된다. 그리고 공유기에 연결된 다수의 서버도 IP를 할당받는다. 공유기의 주소를 외부 IP 각각의 서버의 IP를 내부 IP라고 한다. 포트포워딩은 외부 IP를 통해 접근하여 여러 개의 서버 중 원하는 서버로 고를 수가 있는데, 접근하고자 하는 서버의 포트번호를 설정하여 외부 IP뒤에 포트번호를 붙여 서버에 접근할 수 있다.

### Q. API
A. API는 Application Programming Interface의 약자로 사용자가 원하는 기능을 제공해주는 매개체 역할을 한다.

### Q. P2P
A. 네트워크에 연결된 두 대의 컴퓨터가 클라이언트와 서버의 역할을 동시에 할 수 있어서 서로에게 서비스를 주거나 받을 수 있는 통신 방식을 피어 투 피어 방식이라고 한다. 주로 개인 컴퓨터 간의 파일 공유나 인터넷 전화 등에 활용된다.

### Q. 회선교환 방식/ 패킷교환 방식
A. 네트워크는 패킷교환 방식을 이용하여 여러 대의 컴퓨터와 혼선 없이 데이터를 주고 받을 수 있다. 이메일과 파일과 같은 데이터를 패킷이라는 작은 단위로 분할한 후 주고받는다. 패킷은 자신이 어디로 전달되어야 하는지 알 수 있도록 Address를 가지고 있다.

아날로그 방식의 유선 전화나 3G 방식의 휴대전화는 회선교환 방식을 사용한다. 회선교환 방식은 통신하려는 양측을 연결하기 위해 하나의 통신 경로를 점유한 후 통신하는 방식이라서 기본적으로 일대일 통신만 할 수 있다.

### Q. TCP/IP 4계층
A. TCP/IP 4계층은 OSI 네트워크 모델을 기반으로 실제 통신에 사용되는 인터넷 프로토콜 스택이다. 각 계층은 Application, Transport, Internet, Network Interface 계층이 있다.

### Q. Application Layer
A. 애플리케이션 계층은 웹이나 이메일과 같은 서비스를 제공하는 계층이다. 각 서비스는 자신만의 독자적인 프로토콜을 가지고 있다. 네트워크 계층 모델 중 트랜스포트 이하의 계층들은 데이터 전송을 담당하고 있으므로 데이터 전송 관련 계층을 제외한 모든 영역이 애플리케이션 계층의 범주라고 보면 된다.

### Q. HTTP 
A. HTTP는 인터넷에서 데이터를 주고 받을 수 있는 프로토콜로 클라이언트-서버 구조로 되어있다. 클라이언트는 서비스를 요청하고, 서버는 해당 요청에 대한 결과를 응답함으로써 서로 독립적으로 일한다. 또한 무상태 프로토콜로 단순히 요청에 대한 결과를 응답만 할 뿐 클라이언트 정보를 따로 저장해두지 않는다. 마지막으로 비연결성이다. 클라이언트와 서버가 연결을 계속 유지하고 있으면 그만큼 서버 자원을 소모한다. 그래서 요청에 대한 응답을 완료하면 바로 연결을 끊어 빠른 응답 속도를 보여준다.

### Q. GET/POST
A. GET과 POST 모두 클라이언트에서 서버로 요청을 보내는 HTTP 메소드이다. GET은 특정 리소스에  대한 정보를 요청하기 위해 사용되는 메소드로 보통 URL 끝에 쿼리 스트링으로 요청한 파라미터에 대한 정보를 전달받는다.

POST는 클라이언트에서 서버로 리소스를 생성하거나 업데이트하기 위한 데이터를 보낼 때 사용되는데, 데이터를 HTTP 메시지 바디에 담아서 보낸다. GET과 달리 데이터 전송 시 길이 제한이 따로 없어 용량이 큰 데이터를 보낼 수 있다.

멱등성 관점에서 보면 GET은 멱등이고 POST는 멱등이 아니다. 여기서 멱등이란 연산을 여러 번 적용하더라도 결과가 달라지지 않는 성질을 뜻한다.

### Q. Transport Layer
A. 트랜스포트 계층은 애플리케이션 계층과 인터넷 계층 사이에 위치한다. 인터넷 계층의 역할이 데이터를 수신지 컴퓨터까지 전달하는 것이라면, 트랜스포트 계층의 역할은 컴퓨터가 받은 데이터를 애플리케이션까지 전달하는 것이다. 트랜스포트 계층은 포트 번호로 애플리케이션을 구분하게 된다. 할당된 포트 번호를 참고하여 데이터를 애플리케이션에 전달하게 된다.

### Q. TCP/UDP
A. TCP와 UDP 모두 트랜스포트 계층에서 사용되는 프로토콜이다. TCP는 연결지향형 프로토콜로 신뢰성이 중요한 서비스에 사용된다. 3way handshake 과정을 통해 클라이언트와 서버 간 가상 연결을 확립한 후 데이터를 주고받는다. 또한 IP와 달리 데이터 전달과 순서를 보장해준다.

UDP는 이와 같은 것을 일제히 신경쓰지 않고 데이터를 빨리 보내는 것에만 초점을 둔다. 그래서 데이터가 왜곡되더라도 사람이 잘 인지하지 못하는 영상이나 음성 데이터 전송에 주로 사용한다. UDP 헤더에는 포트 번호만 적혀 있어 하얀 도화지에 비유할 수 있는데, 애플리케이션 계층에서 추가적인 작업을 해주면 TCP처럼 신뢰성 있게 사용할 수 있다.

### Q. UDP를 TCP처럼
A. UDP를 TCP처럼 신뢰성 있게 사용할 수 있는데, 바로 애플리케이션 계층에서 흐름 제어나 혼잡 제어를 구현해서 부족한 신뢰성을 보완할 수 있다. 흐름 제어란 송신측과 수신측의 데이터 처리 속도 차이를 해결하기 위한 기법이다. 수신측이 송신측보다 속도가 빠른 것은 아무 문제가 되지 않지만 반대인 경우에 문제가 발생한다. 이러한 문제를 해결하기 위해 Stop and wait 방식과 슬라이딩 윈도우 기법이 있다. Stop and wait 방식은 매번 전송한 패킷에 대해 확인 응답을 받아야만 그 다음 패킷을 전송하는 방법이며, 슬라이딩 윈도우 기법은 수신 측에서 설정한 윈도우 크기만큼 송신 측에서 확인 응답 없이 세그먼트를 전송할 수 있게 하여 데이터 흐름을 동적으로 조절하여 제어하는 기법이다. 이처럼 슬라이딩 윈도우 기법을 통하여 송신 버퍼의 범위는 수신 측의 여유 버퍼 공간을 반영하여 동적으로 바뀜으로써 흐름 제어를 수행한다.

두 번째로 혼잡 제어는 송신측의 데이터 전달과 네트워크의 처리속도 차이를 해결하기 위한 기법이다. 송신측의 데이터는 지역망이나 인터넷으로 연결된 대형 네트워크를 통해 전달된다. 하지만 이러한 네트워크 상의 라우터가 항상 한가로운 상황은 아니기에 한 라우터에 데이터가 몰릴 경우 라우터는 자신에게 온 데이터를 모두 처리할 수 없다. 이를 해결하기 위해 Slow Start와 Fast Recovery가 있다. Slow Start는 윈도우 사이즈를 2배로 늘리며, 혼잡 현상이 발생하면 창 크기를 1로 떨어뜨린다. (?? 좀 어렵) Fast Recovery는 혼잡한 상태가 되면 창 크기를 1로 줄이지 않고 반으로 줄이고 선형 증가시키는 방식이다.

### Q. Internet Layer
A. 인터넷 계층은 네트워크 인터페이스 계층과 협력하여 다른 컴퓨터에게 데이터를 전달하는 역할을 한다. 인터넷 계층은 IP Address라고 하는 식별자 정보를 실마리로 데이터를 전달할 수 있는 체계를 제공하도록 역할이 구분되어 있다.

송신지, 수신지 컴퓨터는 IP Address로 식별할 수 있다. IP Address 정보를 보고 인터넷 어딘가에 연결된 컴퓨터를 찾아 데이터를 전달한다. 전달 과정에서 문제가 생겨 수신지까지 전달되지 않는 경우가 발생하기도 한다.

쉽게 말해, 라우터를 이용해 최적의 경로를 찾아 목적지 IP Address로 데이터를 전달한다.

### Q. 라우터/라우팅
A. 데이터를 목적지까지 전달하기 위해서는 라우터라고 하는 네트워크 장비가 필요하다. 라우터는 네트워크와 네트워크를 연결하는 역할을 하는데, 하나의 라우터는 데이터를 목적지까지 전달하기 위해 다음 네트워크의 경로를 찾고, 그 경로상에 있는 라우터에게 데이터를 전달을 위임하게 된다. 이런 과정은 최종 목적지를 찾기까지 연쇄적으로 반복되는데, 이렇게 라우터가 목적지의 경로를 찾아 나가는 과정을 라우팅이라고한다.

### Q. Network Interface Layer
A. 네트워크 인터페이스 계층은 네트워크의 하드웨어를 제어하는 부분이다. 상위 계층으로부터 받은 정보를 아날로그 신호로 변환하여 물리적으로 연결된 기기로 전송한다. MAC Address를 사용해서 바로 다음 목적지로 가게 한다. 대표적인 프로토콜로는 IP Address를 통해 MAC Address를 알아내는 ARP가 있다.

### Q. OSI 7계층
A. OSI 7계층은 통신에 사용되는 개념적인 네트워크 모델로 통신 과정을 단계적으로 파악할 수 있다. 통신을 담당하는 5, 6, 7 상위 계층을 통해 데이터가 만들어지고 1, 2, 3, 4 하위 계층에서 데이터를 전달한다.

최상위 계층부터 하향식으로 설명하자면 7계층은 Application 계층으로 사용자가 직접 사용할 수 있는 서비스를 제공한다. 대표적인 프로토콜로는 웹 통신에서 사용하는 http나 파일 전송을 담당하는 ftp가 있다.

6계층은 Presentation 계층으로 전송하는 데이터 포맷을 결정한다. 5계층은 Session 계층으로 두 호스트 사이에서 세션을 열고, 닫고 관리해주는데 대표적으로 SSL/TLS가 있다.

4계층은 Transport 계층으로 데이터 전송 방식을 결정하고, 받은 데이터를 포트 번호를 보고 상위 계층으로 전달해준다. TCP나 UDP와 같은 프로토콜이 있다. 3계층은 Network 계층으로 목적지의 IP 주소까지 데이터를 전달하는데 라우터를 거쳐 최적의 경로를 찾는다.

2계층은 Data Link 계층으로 랜카드에 있는 MAC 주소를 이용해 다음 목적지까지 데이터를 전달한다. 마지막으로 Physical 계층에서는 상위 계층에서 받은 데이터를 아날로그 신호로 변환하여 전선으로 흘려보내고 받은 신호는 디코딩해 비트로 해석한다.