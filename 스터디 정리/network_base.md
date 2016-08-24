# 현우와 네트워크 공부하기  
**by Hyunwoo Kim**  
**Just For _플젝허쉴?_**  

## 용어정리 (Base)
### 네트워크란
*정보의 공유, 자원의 공유를 위해 장비들 끼리 대화를 할 수 있도록 연결 하는 것.*
그렇게 장비가 점점 늘어나 지금의 거대한 네트워크가 탄생

### 인터넷이란
**Inter (연결) + Net (Network)** 로, _여러 개의 네트워크를 묶었다_ 라는 뜻
네트워크를 좀 더 많은 사람들과 정보를 공유하고자 서로 연결하기 시작해 발전한 것이 인터넷의 시작입니다.

### 인터넷의 특징
**하나의 프로토콜만 사용 (TCP/IP, HTTP, UDP, etc...)**


### 인트라넷 (IntraNet)
**Intra (내부) + Net (Network)** 로, _내부의 네트워크_ 라는 뜻


## 용어정리 (Network)
### LAN (Local Area Network)
넓지 않고, 한정된 공간에서 네트워크를 구성하는 것.
Ex) BOB 워룸에 호스트 20개 정도의 네트워크를 구성할 때, LAN을 구축한다고 함

### WAN (Wide Area Network)
넓은 지역의 네트워크를 구성하는 것

### Ethernet
네트워킹의 한 방식. CSMA/CD 라는 프로토콜을 사용해서 통신을 하는 것이 특징
Ex) TokenRing, FDDI, ATM, etc...

### CSMA/CD (Carrier Sense Multiple Access / Collision Detection)
> **대충 알아서 눈치로 대화하자**
>
    1. Carrier 를 보내 네트워크 상의 신호 충돌을 감지한다. (Carrier Sense)
    2. 충돌이 감지될 경우 (Collision Detection), 데이터 전송을 중단하고 기다린다.
    3. 네트워크의 통신이 없을 때, 자기의 데이터를 전송한다.
    4. 1번으로 돌아간다.

네트워크에서 통신할 때, 동시에 여러 컴퓨터가 통신을 시도할 때가 있음. (Multiple Access) 이때의 다중 접근으로 인해 충돌이 발생할 경우, **랜덤한 시간**을 기다리고 다시 정보를 보내게 된다.

### TokenRing
> **한번에 하나의 컴퓨터만 이야기 한다**
>
    1. Token을 받는다.
    2. 자신의 패킷을 보낸다.
    3. 전송이 끝나고 Token을 넘긴다.

주로 IBM 대형 컴퓨터 들이 있는 곳에서 많이 사용한다.

보통 Ethernet의 속도는 **10Mbps**, TokenRing의 속도는**4Mbps, 16Mbps** 정도 된다.

### UTP Cable
TP : Twisted Pair 즉, **꼬인 케이블**을 의미한다.
UTP : Unshielded (**감싸지 않은**) TP
STP : Shield로 절연체를 이용해 **감싼** TP

Category 별로 구분한다.
1. Category 1: 주로 전화망에 사용
2. Category 2: 데이터를 최대 4Mbps 속도로 전송
3. Category 3: 10 Base T 네트워크에 사용되는 케이블
4. Category 4: TokenRing 네트워크에서 사용하는 케이블. 최대 16Mbps 속도
5. Category 5: 최대 100Mbps 지원하는 Fast Ethernet용으로 사용. 기가비트 표준이 완성되어 기가비트 속도를 지원함

케이블 종류를 표기할 때, **10 Base T** 로 표기한다.
- **10**: 10Mbps 속도를 지원하는 케이블
- **Base**: Baseband용 케이블. 디지털 케이블을 의미한다. **Broad**의 경우 아날로그 케이블을 의미한다.
- **T**: TP 케이블을 의미한다. 우리가 사용하는 UTP 케이블과 같다. 만약 이 자리에 숫자가 올 경우, 최대 통신거리를 나타낸다. (숫자 **5** == **500M**)

아래 몇 가지 표기 예시를 보며 개념을 잡자


>## TODO: Need Add Content

- 10 Base T
	- 10Mbps 속도
	- 최대 전송거리 100M
	- UTP 케이블
	- Category 3,4,5 사용
	- RJ 45 사용

- 10 Base FL
	- 광케이블 (FL, Fiber-Optic)
	- 10 Mbps 속도
	- ST 커넥터를 이용해 연결 Single or Multi Mode Cable 사용
    
- 10 Base 2
- 10 Base 5
- 100 Base TX
- 100 Base T2
- 100 Base T4
- 100 Base FX
- 100 Base SX
- 100 Base T


## _"Real"_ Network
### OSI 7 Layer
**OSI** == Open Systems Interconnection

아래 문구를 보며 7계층을 알아보자

**_`P`lease `D`o `N`ot `T`ouch `S`teve's `P`retty `A`lligator_**

>**P** hysical : 물리 

* 데이터를 전기적 신호로 변환하여 케이블을 이용해 전송
* 통신단위는 Bit 기준이고, 단순히 데이터만 전송
* **Cable, Repeater, Hub**

---

>**D** ata Link : 데이터 링크 

* 물리계층을 통해 송수신되는 신호의 오류와 흐름을 제어
* 정보의 신뢰성을 보장
* 오류, 재전송, MAC
* **Bridge, Switch**

---

>**N** etwork : 네트워크

* 데이터를 목적지까지 빠르게 전달
* 패킷의 경로를 선택하여 해당 경로로 패킷을 보냄.
* **Router**

>**T**: Transport 전송

>**S**: Session 세션

>**P**: Presentation 표현 

>**A**: Application 응용

---

### MAC (Media Access Control)
네트워크 상에서 서로 구분하기 위해 사용하는 주소






>## TODO: Need Add Content
> ---	
	* OSI 7 Layer
	* TCP/IP
		* IP Address Info
			* Subnet Mask
			* Bit Mask
			* Subneting
		* MAC Address Info


> ---
	* Multicast
	* Unicast
	* BroadCast

> ---
	* Bridge
	* Switch
		* Learning
		* Flooding
		* Forwarding
		* Filtering
		* Aging
	* Looping
		* Spanning Tree Protocol
	* Fault tolerant
	* Load Balancing

> ---
	* Router
    * Routing Algorithm
    	* RIP
    	* EIGRP
    	* OSPF
    * QoS (Quality of Service)






































