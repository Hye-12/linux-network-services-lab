# DNS Commands

## BIND DNS Server 설치

```bash
dnf install -y bind bind-utils bind-libs
```

## named 설정파일 수정

```bash
vi /etc/named.conf
```

## Forward Zone 파일 생성

```bash
cp /var/named/named.localhost /var/named/forward.zone
```

## Reverse Zone 파일 생성

```bash
cp /var/named/named.loopback /var/named/reverse.zone
```

## Forward Zone 파일 수정

```bash
vi /var/named/forward.zone
```

## Reverse Zone 파일 수정

```bash
vi /var/named/reverse.zone
```

## named 설정 문법 검사

```bash
named-checkconf
```

## Forward Zone 문법 검사

```bash
named-checkzone hye12.local /var/named/forward.zone
```

## Reverse Zone 문법 검사

```bash
named-checkzone 0.0.10.in-addr.arpa /var/named/reverse.zone
```
## Forward Zone, Reverse Zone 권한 수정
```
chmod 640 /var/named/{forward_zone,reverse_zone}
named 서비스가 zone 파일을 읽을 수 있도록 권한 수정
```

## Firewall Open

```bash
firewall-cmd --permanent --add-service=dns
firewall-cmd --reload
```

## named 서비스 실행

```bash
systemctl enable --now named
```

## 서비스 상태 확인

```bash
systemctl status named
```

## DNS 서비스 로그 확인

```bash
journalctl -xeu named
```

## DNS 조회 테스트

```bash
nslookup
```
```text
www.hye12.local
hye12.local
ftp.hye12.local
blog.hye12.local
intra.hye12.local
```
```bash
nslookup 10.0.0.11
nslookup 10.0.0.12
nslookup 10.0.0.13
```
