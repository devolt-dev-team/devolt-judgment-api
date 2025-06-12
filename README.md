# 🚀 Devolt 코드 채점 API 서버

**Devolt 채점 시스템 API 서버입니다.**
- 주로 Spring Boot와 Redis(Broker)를 중개하는 역할을 합니다.
- 코드 채점 작업 등록/실행/중지 API를 제공합니다.
- 코드 채점 작업의 정보를 Redis를 사용해 유지합니다.
- 실제 코드 실행 작업은 Celery Worker 애플리케이션이 처리합니다.

<br /><br />




## 🧱 채점 요청/응답 처리 구조
### 채점 등록/실행/중단 요청
```
End User -> Spring Boot -> Flask API Server -> (Redis -> Flask API Server) -> Spring Boot -> End User
```
- Redis를 통해 API 요청에 대한 Task를 생성하고 WebHook 방식으로 처리합니다.

<br /><br />




## ✨ 주요 기능

- REST API 엔드포인트 제공
- 코드 채점 요청 처리 및 검증
- Redis 태스크 큐에 작업 등록
- 채점 결과 웹훅 콜백 처리
- HMAC 기반 API 키 인증
