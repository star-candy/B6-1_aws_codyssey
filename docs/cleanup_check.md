### 리소스 정리 (Cleanup)

- 과금 방지를 위해 생성 역순으로 리소스를 삭제하고 체크리스트를 작성합니다.

- [ ] **EC2 인스턴스:** 상태가 `Terminated`(종료됨)인지 확인 완료
- ![alt text](/images/imagea.png)
- [ ] **EBS 볼륨:** 인스턴스 종료 시 함께 삭제되도록 설정됨
- ![alt text](/images/imagea-1.png)
- [ ] **Elastic IP:** `Release`(릴리즈/할당 해제) 확인 완료 (해당 시)
- ![alt text](/images/imagea-2.png)
- [ ] **Internet Gateway:** VPC에서 `Detach` 후 삭제 확인 완료
- ![alt text](/images/imagea-3.png)
- ![alt text](/images/imagea-4.png)

- [ ] **VPC:** 실습용 VPC 삭제 확인 완료
- ![alt text](/images/imagea-5.png)