# TCP/IP 4계층

## TCP\(Transmission Control Protocol\)

TCP/IP는 데이터가 의도된 목적지에 닿을 수 있도록 보장해주는 통신 규약이다. TCP/IP는 인터넷의 기본 통신 언어로, 기본적으로 TCP/IP를 사용하면 한 컴퓨터가 데이터 패킷을 컴파일하고 올바른 위치로 전송하여 인터넷을 통해 다른 컴퓨터와 통신할 수 있다.

TCP는 기본적으로 IP와 함께 사용되며, 그런 이유로 TCP/IP라 부른다. IP는 호스트 사이의 데이터 교환을 목적으로 만들어진 프로토콜로, 패킷을 목적까지 보내는 일만 담당한다. 즉, 네트워크상에서 발생할 수 있는 데이터 누락, 패킷의 순서 뒤바뀜 등의 데이터 교정과 관련된 기능을 가지진 않는다.

그래서 만들어진 것이 TCP 프로토콜이다. IP 프로토콜의 상위 레벨 프로토콜로써, IP가 제공하지 못하는 기능 즉, 데이타 누락검사 패킷순서 뒤바뀜 등 데이터 교정과 관련된 기능을 수행한다.

최상위 계층인 TCP는 많은 양의 데이터를 가져와 패킷으로 컴파일 한 다음 동료 TCP 계층에서 수신하도록 전송하여 패킷을 유용한 정보 혹은 데이털 바꾸는 역할을 한다. TCP는 전달받은 패킷을 재조립하고, 패킷에 손상이 있거나 손실된 패킷이 있다면 재전송을 요청하는 패킷을 전송하여 재전송 받는다.

#### 프로토콜이란 ?

컴퓨터와 네트워크 기기가 상호간에 통신하기 위해 정해둔 규칙

#### 패킷이란 ?

데이터를 일정한 크기로 자른 다음 인터넷에서 정보를 전달하는 단위

## IP\(Internet Protocol\)

인터넷에서 컴퓨터의 위치를 찾아 데이터를 전송하기 위해 지켜야 할 규약이다. 전 세계 수십억대의 컴퓨터가 인터넷을 원활하게 이용하기 위해 서로의 신원을 확인할 수 있도록 주소를 부여했는데, 이 주소를 IP 주소라고 한다. IP는 4개의 숫자로 구성되며 숫자의 크기에 따라 IPv4\(32비트, 각 숫자는 1바이트\), IPv6\(128비트, 각 숫자는 4바이트\)로 나뉜다. 일반적으로 IPv4는 10진수로 표현하며 각 자리는 .으로 구분하고, IPv6는 각 자리를 4자리 16진수로 표현하며 각 자리는 :로 구분한다. 맨 아래 계층인 IP는 올바른 목적지를 찾는 패킷 GPS 역할을 한다. 지도의 관점에서 IP를 생각하면 IP 계층은 고속도로에서 운전하는 자동차와 마찬가지로 각 패킷은 게이트웨이 컴퓨터\(도로 표지판\)을 통과하여 패킷을 올바른 목적지로 전달하는 역할을 한다.

## TCP/IP의 4계층

![](../.gitbook/assets/image%20%285%29.png)

### Layer 1 : 네트워크 인터페이스 계층\(Network Access Layer\)

* OSI 7계층의 물리 계층과 데이터 링크 계층에 해당 
* 노드와 노드 사이에 신뢰성 있는 데이터 전송을 담당하는 계층 
* 물리적인 주소로 MAC을 사용
* 기본적으로 에러 검출 및 패킷의 프레임화를 담당
* 주요 프로토콜: Ethernet, Token Ring, Frame Relay, ATM

### Layer 2 : 인터넷 계층\(Internet Layer\)

* OSI 7계층의 네트워크 계층에 해당
* Addressing, Packaging, Routing 기능 제공
* 네트워크상 최종 목적지까지 정확하게 연결되도록 연결성 제공
* 주요 프로토콜: IP, ARP, RARP, ICMP, IGMP

### Layer 3 : 전송 계층\(Transport Layer\)

* OSI 7계층의 전송 계층에 해당
* 응용 계층의 세션과 데이터그램 통신 서비스 제공
* 통신 노드 간의 연결을 제어하고, 프로세스 사이에 신뢰성 있는 데이터 전송을 담당
* 주요 프로토콜: TCP, UDP

### Layer 4 : 응용 계층\(Application Layer\)

* OSI 7계층의 세션 계층, 표현 계층, 응용 계층에 해당
* 브라우저가 직접 상호작용하는 레이어로 데이터를 최초로 받는 곳
* 동작하기 위해 전송 계층의 주소, 즉 포트 번호를 사용
* 다른 계층의 서비스에 접근할 수 있도록 애플리케이션 제공
* 애플리케이션들이 데이터를 교환하기 위해 사용하는 프로토콜 정의
* TCP/UDP 기반 응용프로그램 구현 시 사용
* 주요 프로토콜: FTP\(20, 21\), HTTP\(80\), SSH\(22\), SMTP\(25\), DNS\(53\), POP3\(110\), Telnet\(23\)

## 참고

* [네트워크 기초 - OSI 7 계층과 TCP/IP 계층](https://snyung.com/content/2020-08-31--네트워크-기초-OSI-7-계층과-TCP-IP-계층)
* [TCP/IP란 무엇인가 ?](https://coding-factory.tistory.com/613)
* [\[네트워크\] TCP/IP 계층 기본 개념\(네트워크 계층, 인터넷 계층, 전송계층, 응용계층\)](https://reakwon.tistory.com/68)
* [TCP/IP 4계층\(TCP/IP 4 Layer\)](https://m.blog.naver.com/soojin_2604/221950485931)

