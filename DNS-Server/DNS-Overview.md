# DNS Overview

## DNS란?

DNS(Domain Name System)는 도메인 이름을 IP 주소로 변환해주는 서비스이다.

예시:

```text
www.google.com → 142.x.x.x
```

사용자는 도메인 이름으로 접근하고,
시스템은 DNS를 통해 실제 IP 주소를 조회한다.

---

## 실습 목적

- BIND(named) DNS 서버 구축
- Primary DNS Server 구성
- Secondary DNS Server 구성
- Zone Transfer 설정
- Forward Zone / Reverse Zone 구성
- nslookup을 통한 동작 확인

---

## 실습 환경

| Host | Role | IP |
|---|---|---|
| rocky9-2 | Primary DNS | 10.0.0.12 |
| rocky9-1 | Secondary DNS | 10.0.0.11 |
| rocky9-3 | Secondary DNS | 10.0.0.13 |

---

## 주요 구성 내용

- `hye12.local` 정방향 영역 구성
- Reverse Zone 구성
- Zone Transfer 설정
- Master-Slave 구조 구성
- NS / A / PTR 레코드 설정

---

## 테스트 내용

- `nslookup` 동작 확인
- Zone Transfer 동기화 확인
- Reverse Lookup 확인
- 보조 DNS 동기화 확인
- named 서비스 상태 확인
