# Mail Overview

## Mail Server란?

Mail Server는 전자메일 송수신 서비스를 제공하는 서버이다.

주요 기능:
- 메일 송신 (SMTP)
- 메일 수신 (POP3 / IMAP)
- 사용자 메일함 관리

---

## 실습 목적

- Mail Server 구축
- SMTP / POP3 / IMAP 동작 확인
- DNS MX Record 연동
- 메일 송수신 테스트
- Thunderbird를 이용한 메일 클라이언트 테스트

---

## 실습 환경

| Host | Role | IP |
|---|---|---|
| rocky9-3 | Mail Server | 10.0.0.13 |

---

## 사용 프로토콜

| Protocol | Port | Description |
|---|---|---|
| SMTP | 25 | 메일 송신 |
| POP3 | 110 | 메일 수신 |
| IMAP | 143 | 메일 수신 및 동기화 |

---

## DNS 설정

```text
mx1.hye12.local → 10.0.0.13
```

MX Record를 이용해 메일 서버 지정

---

## 테스트 내용

- Telnet SMTP 연결 확인
- Thunderbird 메일 송수신 테스트
- MX Record 조회 확인
- 메일 Queue 확인
- SMTP 인증 테스트
