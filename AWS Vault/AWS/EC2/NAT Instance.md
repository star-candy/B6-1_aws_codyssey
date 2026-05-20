#### [[EC2]] 인스턴스 기반으로 외부 통신망과 연결 기능

- [[NAT 게이트웨이]] 서비스를 EC2 인스턴스를 통해 직접 구현
- 고비용 NAT 게이트웨이의 대안으로 사용
- 단 가용성과 유지관리 측면에서 NAT 게이트웨이에 비해 낮은 성능

#### 생성 후 Networking - destination checking 해제할 것 
- -> Instance는 기본적으로 본인이 목적지인 트레픽을 받아들임
- -> 단 Nat Instance는 트레픽 중간자 역할을 하기에 해제 필요

#### 생성 후 private 서브넷 라우팅 테이블에 Nat Instance 추가 필요
- 라우팅 테이블 타겟을 Instance(NAT Instance)로 추가할 것
- 테이블 추가해야 내 외부로 트레픽 진입 가능

#### 사용법
##### iptables 설치 및 활성화**

`sudo yum install iptables-services -y`  
`sudo systemctl enable iptables`  
`sudo systemctl start iptables`  

##### IP 포워딩 활성화** 

1.  vi 편집기를 통한 구성파일 생성

`sudo vi /etc/sysctl.d/custom-ip-forwarding.conf`

2.  구성파일에 입력할 활성화 명령어

`net.ipv4.ip_forward=1`

3. 파일 저장 후, 구성 파일 적용 명령어
    

`sudo sysctl -p /etc/sysctl.d/custom-ip-forwarding.conf   `

##### 네트워크 인터페이스 이름을 확인 명령어**

`netstat -i`

**NAT 구성 명령어**

`sudo /sbin/iptables -t nat -A POSTROUTING -o 인터페이스이름 -j MASQUERADE`  
`sudo /sbin/iptables -F FORWARD`  
`sudo service iptables save`