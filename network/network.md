## 네트워크

#### 1. OSI 7 layer와 각 계층 설명
1. Physical layer: 물리적 특성을 이용해 통신 케이블로 데이터를 전송. (단위: bit) (장비: 케이블, 리피터, 허브)  
1. Data Link layer: MAC address 기반으로 물리적 연결 과정에서 생기는 오류 검출, 흐름 제어 등을 수행. (단위: frame) (ex: 이더넷)  
1. Network layer: 논리적 주소인 IP address를 담당하며, 패킷의 전달 경로를 결정. (단위: Packet) (ex: Router)   
1. Transport layer: End to End간 메시지 전송에서 오류 검출과 흐름 제어를 담당. (단위: Segment) (ex: TCP, UDP)  
1. Session layer: 양쪽 Host 간 연결을 수립/유지/종료시키는 역할  
1. Presentation layer: 코드 간의 번역을 담당.  
1. Application layer: 사용자에게 통신을 위한 서비스 제공. 인터페이스 역할.

#### 2. TCP/IP 프로토콜과 각 계층 설명
#### 3. TCP의 특징
- 점대점 : 두 노드간의 통신
- 전이중 : 양방향 통신이 가능
- 흐름제어 : 수신측의 처리량을 고려하여 데이터를 전송
- 혼잡제어 : 특정 네트워크 구간에 데이터가 몰리지 않도록 처리


#### 4. SSL   
Secure Socket Layer로 인터넷을 통해 전달되는 정보를 보호하기 위해 개발한 통신 규약. HTTPS는 HTTP 에 SSL과 같은 보안 계층을 제공한다.

#### 5. 3way hand shaking
#### 6. 4 way hand shaking
- Client -> Server : FIN
- Server -> Client : ACK
- Server -> Client : FIN
- Client -> Server : ACK

#### 7. TCP 연결 끊김 탐지  
- timeout : 일정한 시간 동안 상대방으로부터 메시지(ex. FIN)가 오지 않으면 연결 종료.  
- keep alive : 주기적으로 상대방에게 메시지를 보내 응답이 오는지 확인함으로써 상대 호스트 연결이 유지되고 있는지 확인.

#### 8. HTTP의 특징
#### 9. www.example.com까지의 접속 과정
1. 호스트 네임을 통해 DNS에서 IP주소를 받아온다.
2. IP주소를 통해 서버와 커넥션을 맺는다.
3. 서버는 받은 요청에 따라 이를 처리하고 브라우저가 볼 수 있는 HTML을 구성해 브라우저에게 준다.
4. 브라우저는 HTML을 해석해 화면에 띄운다.

#### 10. Get과 Post의 차이점
- GET: 데이터 조회, 쿼리로 요청 데이터를 전송하며, 외부에 노출된다.  
- POST: 데이터 추가(생성), request body 안에 전송할 데이터를 넣어 전송한다. 데이터는 외부에 노출되지 않는다.  

#### 11. TCP와 UDP의 차이

-----

#### 12. SYN Flooding 공격 설명, 방어 방법

#### 13. 로드 밸런싱

#### 14. 싱글스레드 서버와 멀티스레드 서버 예시

#### 15. 흐름제어 방식이 뭔지 그리고 대표적인 방식 설명

#### 16. 서브네팅이란?

#### 17. ARP란?

