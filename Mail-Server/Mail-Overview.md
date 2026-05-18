# Mail Overview

## Mail Server란?

Mail Server는 전자메일 송수신 서비스를 제공하는 서버이다.

주요 기능:
- SMTP : 메일 송신
- POP3 / IMAP : 메일 수신
- 사용자 메일함 관리

---

## 실습 목적

- Sendmail 기반 Mail Server 구축
- Dovecot을 이용한 POP3 / IMAP 구성
- DNS MX Record 연동
- Thunderbird 메일 클라이언트 테스트
- 메일 송수신 및 인증 확인

---

## 실습 환경

| Host | Role | IP |
|---|---|---|
| rocky9-3 | Mail Server | 10.0.0.13 |

---

## 사용 서비스

| Service | Description |
|---|---|
| Sendmail | SMTP 메일 송신 서비스 |
| Dovecot | POP3 / IMAP 메일 수신 서비스 |
| Thunderbird | 메일 클라이언트 |

---

## Mail Service Port

| Protocol | Port |
|---|---|
| SMTP | 25 |
| POP3 | 110 |
| IMAP | 143 |

---

## DNS 설정

```text
mx1.hye12.local → 10.0.0.13
```

MX Record를 이용해 Mail Server 지정

---

## 주요 설정 내용

- Sendmail SMTP 설정
- Dovecot POP3 / IMAP 설정
- SMTP Relay 설정
- Mail 계정 생성
- Thunderbird 메일 송수신 테스트

---

## 테스트 내용

- `telnet mx1.hye12.local 25`
- Thunderbird 메일 송수신 테스트
- MX Record 조회 확인
- SMTP 인증 확인
- Mail Queue 확인
