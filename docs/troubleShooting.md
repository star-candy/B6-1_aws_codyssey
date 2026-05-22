## 증상 : 인스턴스 생성 및 Amazon machine image 할당 시 아래 오류메시지 발생
```
AMI ID가 유효하지 않습니다. AMI가 더 이상 존재하지 않거나 다른 계정 또는 리전 전용일 수 있습니다.
```
- ![alt text](/images/image-10.png)

## 원인 가설
- 해당 AMI가 서울 리전에 존재하지 않을 가능성
- AMI 설정 관련 권한이 설정되지 않았을 가능성

## 검증 방법
- root 계정에서 에러가 발생하는지 확인
    - root 계정에서는 정상적으로 AMI 설정이 존재함
    - ![alt text](/images/image-11.png)


## 조치 내용
- IAM 그룹 정책을 추가한다.
    - "ec2:DescribeImages" 권한을 추가한다.
    - "ec2:DescribeInstanceTypes" 권한을 추가한다.
    - ![alt text](/images/image-12.png)
    
## 결과
- 정상적으로 AMI가 조회되고 EC2 인스턴스 생성이 완료됨
- ![alt text](/images/image-13.png)

## 재발 방지
- 최소 권한 원칙으로 IAM 그룹 정책 구성 시 생성 및 조회 권한을 짝을 이뤄 구성할 것.