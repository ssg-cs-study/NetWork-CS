# CS스터디 5장



## 💫라우터/L3 스위치 - 3계층

### 1️⃣라우터(Router)란

- 패킷을 목적지까지 전달하기 위해 다음 네트워크 지점을 결정하는 3계층 네트워크 장비이다.
- 라우터는 여러 개의 통신 회선에 연결되는 특수한 컴퓨터로 한 회선으로부터 받은 패킷들을 조사하여 그 패킷의 최종 목적지에 가까운 최적의 경로로 패킷을 라우팅하도록 한다.
- 라우터의 목적은 **서로 다른 네트워크**를 **연결**하는 것이다.
    
    → 내부 네트워크와 외부 네트워크를 연결시킨다.
    
- LAN과 LAN또는 LAN과 WAN을 연결한다.
- 라우터는 자신이 모르는 목적지 주소를 가진 패킷은 버린다.그렇기때문에 충분한 경로 정보를 가지고 있어야 라우터가 정상작동할 수 있다.

<image src="https://github.com/ssg-cs-study/NetWork-CS/blob/main/%EC%8B%A0%EC%98%81/image/cs_study_1.png">

※라우팅(Routing)이란?

-라우팅은 패킷을 출발지에서 목적지로 전달하는 경로를 결정하는 프로세스이다.

-경로를 결정하는 전체 프로세스를 나타내며 아래의 경로지정등의 개념을 포괄하는 개념이다.

※포워딩(Forwarding)이란?

-포워딩은 라우팅을 통해 목적지를 결정한 후 실제로 목적지로 전송하는 단계를 의미한다.

### 2️⃣라우터의 경로지정

- 라우터는 경로정보를 수집하여 라우팅 테이블을 생성하고 패킷이 라우터에 도착하면 패킷의 도착지 IP주소를 확인해 경로를 지정하고 패킷을 포워딩**(Forwarding)**한다.
- 라우터의 포워딩은 두 가지 역할로 나눌수 있는데 먼저 **경로 정보를 얻는 역할**과 **얻은 경로 정보를 확인하고 패킷을 포워딩하는 역할**이다.
- 라우터는 자신이 얻은 경로 정보를 라우팅 테이블에 포함시키고 패킷을 포워딩할때 라우팅 테이블을 확인하고 패킷을 포워딩한다.
- 라우터가 경로 정보를 얻는 방법은 크게 3가지가 있다.

> **1. 다이렉트 커넥티드(Direct Connected)**
> 
> 
> -IP주소를 입력할때 사용된 IP주소와 서브넷 마스크로 해당 IP주소가 속한 네트워크 주소 정보를 알수 있다.이때 라우터는 해당 네트워크에 대한 라우팅 테이블을 자동으로 생성한다.
> 

<image src="https://github.com/ssg-cs-study/NetWork-CS/blob/main/%EC%8B%A0%EC%98%81/image/cs_study_2.png">

※해당 네트워크 설정을 삭제하지 않는 이상 사라지지 않는다.

> **2.스태틱 라우팅(Static Routing)**
> 
> 
> -관리자가 경로를 직접 지정해 입력하는 것
> 

<image src="https://github.com/ssg-cs-study/NetWork-CS/blob/main/%EC%8B%A0%EC%98%81/image/cs_study_3.png">


> **3.다이나믹 라우팅(Dynamic Routing)**
> 
> 
> -스태틱 라우팅의 경우 관리자가 직접 경로를 설정해야하기때문에 관리하기가 번거롭다.
> 
> -다이나믹 라우팅은 라우터끼리 경로정보와 상태정보를 교환하여 네트워크 정보를 학습한다.
> 
> -주기적으로 교환하거나 상태 정보가 변경될때마다 정보를 교환하기 때문에 상황을 바로 인지하여 패킷을 포워딩할수 있다.
> 
> -장애발생시 관리자의 개입없이 라우터끼리의 정보교환만으로 경로를 우회할수 있다.
> 

<image src="https://github.com/ssg-cs-study/NetWork-CS/blob/main/%EC%8B%A0%EC%98%81/image/cs_study_4.png">

↑자신이 광고할(옆 라우터에게 전달할)네트워크를 선언한다.

```
라우터는 패킷을 전송할때는 전체 경로가 아닌 다음 라우터까지만의 
경로를 고려한다.다음 라우터까지 패킷을 전송하면 그 다음 라우터가
다음 라우터까지의 최적의 경로로 포워딩할것이기 때문이다.
```

<image src="https://github.com/ssg-cs-study/NetWork-CS/blob/main/%EC%8B%A0%EC%98%81/image/cs_study_5.png">

### 4️⃣라우팅 프로토콜

- 라우팅 프로토콜이란 라우터간에 라우팅 정보교환 및 라우팅 테이블 생성 및 유지관리를 하는 프로토콜이다.
- 라우팅 프로토콜을 통해 라우터끼리 자동으로 경로 수집과 전달을 한다.
- 라우터끼리 주기적으로 또는 변화가 발생할 경우 경로 정보를 교환하므로 장애발생시 대체 경로를 찾는 작업을 자동으로 수행한다.
- 라우팅 프로토콜을 유니캐스트 라우팅 프로토콜과 멀티캐스트 라우팅 프로토콜로 나뉘고 일반적인 라우팅 프로토콜은 유니캐스트 라우팅 프로토콜을 의미한다.
    - 유니캐스트 라우팅 프로토콜 → 다음 라우터까지의 경로만 고려하여 경로를 설정
    - 멀티캐스트 라우팅 프로토콜 → 발신지까지 고려하여 경로설정

### 5️⃣IGP와 EGP

- 유니캐스트 라우팅 프로토콜은 역할과 동작원리에 따라 다시 IGP와 EGP로 나뉜다.
- IGP는 AS내에서 통신할때 사용하는 프로토콜이고 EGP는 AS간 통신에 사용하는 라우팅 프로토콜이다.

※AS(Autonomous System) : 동일한 정책으로 관리되고 있는 라우터와 네트워크의 그룹(?),라우터로 상호접속이 되어있는 여러개의 네트워크 집합

→ KT,LG U+,SKT등의 통신사는 하나이상의 AS를 운영한다.

<image src="https://github.com/ssg-cs-study/NetWork-CS/blob/main/%EC%8B%A0%EC%98%81/image/cs_study_6.png">

- IGP프로토콜로는 OSPF, EIGRP, RIP, IS-IS등이 있다.
- IGP의 OSPF의 경우 네트워크를 AREA단위로 나누어 구분하고 AREA 0(Backbone Area)를 통해 모든 AREA들이 통신을한다.(→다른 AREA들을 연결시켜주는 경계 라우터)

### 기타등등

- 브로드캐스트 컨트롤(Broadcast Control)

→2계층 스위치의 경우 도착지 주소를 모르면 모든 네트워크 주소로 패킷을 전송하고 이런 경우 네트워크 성능에 무리를 줄수 있다.

→라우터의 경우 도착지 정보가 있는 경우만  통신을 허용하고 도착지 정보가 없는 경우 해당 패킷을 버리기때문에 위와 같은 플러팅 작업으로 네트워크 성능에 무리를 주지 않는다.
