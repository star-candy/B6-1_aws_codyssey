#### 서버 앞에서 직접 접근을 막는 인스턴스
#### 보안 위해 private 서브넷에 EC2 생성 시 Bastion Host 사용

- public 서브넷에 EC2 사용 시 보안 취약 증가
- EC2를 private, Bastion Host를 public에 배치하여 이상 접근에 대한 안전망 구축
- EC2, Bastion Host 모두 각각의 보안 그룹 필요
- EC2는 Bastion Host 보안 그룹에 대해서만 접근 허용하는 방식으로 사용

![[Bastion Host 이미지.png]]