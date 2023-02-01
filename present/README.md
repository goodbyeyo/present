# 선물하기 프로젝트

<br>

## 1. branch List

| branch | 특이 사항 |
|---|:---:|
| base/implements | |
| api/retrofit | 해당 branch 에서는 aws AMI 계정 발급 후 application.yml 에 반영해야 함 |
| message/aws-sqs | 해당 branch 에서는 aws AMI 계정 발급 후 application.yml 에 반영해야 함 |

## 2. 프로젝트 실행 순서
1. [주문 프로젝트]의 order/expand-gift-with-sqs 브랜치를 로컬에서 사전에 실행시켜야 합니다
2. aws AMI 계정 발급 후 application.yml 에 반영해야 합니다
<br>

## 3. API 호출 순서 
1. gift 서버에서 **선물하기 등록 API** 호출
2. gift 서버에서 **선물하기 결제중 상태로 변경 API** 호출
3. order 서버에서 **선물하기 주문 결제 처리 API** 호출 (이 때, aws-sqs 에 메시지가 발행됨)
4. gift 서버의 SqsListener 가 메시지를 읽고 해당 주문을 ORDER_COMPLETE 으로 변경
5. gift 서버에서 **선물하기 수락 상태로 변경 API** 호출
<br>


