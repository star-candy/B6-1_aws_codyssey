#### Eliastic Compute Cloud - 가상 서버 호스팅 서비스

- 대여한 가상 서버 = EC2 인스턴스
- 빠른 배포 및 확장, 유연성 높은 방식(실제 서버 구현에 비해 간편)
- [[키페어]]를 통해 EC2 인스턴스에 접속 가능(높은 보안성 유지 가능)
- OS 환경 템플릿(AMI) 통해 기본적인 OS 구동 설정 지정 가능
- 데이터 저장 위해 [[EC2 스토리지]] 사용
- [[EC2 Type]]에 따라 여러 가상 컴퓨터 설정 존재
- 다양한 [[EC2 구매 옵션]]으로 비용 절감 가능

- EC2 서버 접속 2가지 방식 (퍼블릭 서브넷 사용 시)
- 1. 서버 퍼블릭 IP, 키페어 통해 콘솔에서 ssh 명령
- 2. 인스턴스 창에서 Connect 통한 연결 가능
- [[EC2와 IP의 관하여]]
#### 보안 위해 private 서브넷에서 EC2 생성 시 [[Bastion Host]] 사용
- Network Setting에서 public ip 할당 disable
- 소스 타입 source를 Bastion Host 보안그룹으로 지정
- -> Bastion host의 접근만 허용하는 방식
#### private 서브넷 Ec2 접근 방식
1. [[Bastion Host]]에서 키페어 통해  private EC2에 접속(sudo ssh -i 키페어 ec2-user@private IP)
	-> 동일 VPC 내에 존재하기에 private ip로 접근 가능
2. [[Instance Connect Endpoint]] 사용

#### advanced detail - User data 통해 서버 배포 자동화 가능 
- user data 항목에 기본 설정, 배포 등 명령어 추가 시 자동 실행 
- 부트스트랩이라고 부름
- 초기 부팅시 한번만 실행되는 영역

#### [[로드밸런서]]통해 여러 인스턴스에 적절히 요청 분배 가능
- 고가용성, 높은 확장성, 에러 대처 등에 용이한 사용방식

#### [[배치그룹]] 통해 인스턴스 배치 방식 제어 가능
- 속도, 안정성에 따라 다양 방식 제공