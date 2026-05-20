#### Private 서브넷에 생성, Bastion Host로 막힌 EC2에 바로 접근 가능
- private 서브넷에 경우 외부에서 Connect가 기본적으로 불가
- private EC2 Connect시 옵션으로 설정 가능
- 생성 시 보안그룹을 Bastion Host로 지정
- 접속 로그 및 접속 시간 명시로 높은 보안 유지 가능