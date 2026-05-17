# DNS Master - Slave

## Primary DNS Server

| Server | IP |
|---|---|
| ns1.hye12.local | 10.0.0.12 |

Primary DNS Server는 원본 Zone 데이터를 관리한다.

---

## Secondary DNS Server

| Server | IP |
|---|---|
| ns2.hye12.local | 10.0.0.11 |
| ns3.hye12.local | 10.0.0.13 |

Secondary DNS Server는
Primary DNS Server로부터 Zone Transfer를 통해 데이터를 복사한다.

---

## Zone Transfer

Primary DNS Server 설정:

```conf
allow-transfer { 10.0.0.11; 10.0.0.13; };
```

Secondary DNS는 named 서비스 재시작 시
Primary DNS로부터 Zone 데이터를 동기화한다.

---

## 테스트

- nslookup 확인
- 보조 DNS 동기화 확인
- reverse lookup 확인
