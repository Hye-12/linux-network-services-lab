# Mail Commands

## hosts 파일 설정

```bash
vi /etc/hosts
```

```text
10.0.0.13    rocky9-3
```

## Mail 사용자 생성

```bash
useradd x
useradd y
passwd x
passwd y
```

## Sendmail / Dovecot 설치

```bash
dnf install -y sendmail sendmail-cf dovecot
```

## Sendmail 설정파일 수정

```bash
vi /etc/mail/sendmail.mc
```

- 56, 57번 줄 `dnl` 제거
- 121번 줄 `Addr=127.0.0.1` 삭제

## sendmail.cf 적용

```bash
m4 /etc/mail/sendmail.mc > /etc/mail/sendmail.cf
```

## local-host-names 설정

```bash
vi /etc/mail/local-host-names
```

```text
mx1.hye12.local
hye12.local
rocky9-3
```

## Relay 허용 설정

```bash
vi /etc/mail/access
```

```text
Connect:10.0.0.0/255.255.255.0    RELAY
Connect:mx1.hye12.local           RELAY
Connect:hye12.local               RELAY
Connect:rocky9-3                  RELAY
```

## access DB 적용

```bash
makemap hash /etc/mail/access < /etc/mail/access
```

## mail 그룹에 사용자 추가

```bash
vi /etc/group
```

```text
mail:x:12:x,y
```

## Sendmail 서비스 실행

```bash
systemctl enable --now sendmail
```

## Dovecot 설정파일 수정

```bash
vi /etc/dovecot/dovecot.conf
vi /etc/dovecot/conf.d/10-auth.conf
vi /etc/dovecot/conf.d/10-mail.conf
vi /etc/dovecot/conf.d/10-master.conf
vi /etc/dovecot/conf.d/10-ssl.conf
```

## Dovecot 서비스 실행

```bash
systemctl enable --now dovecot
```

## Firewall Open

```bash
firewall-cmd --permanent --add-port={25,110,143}/tcp
firewall-cmd --reload
```

## 서비스 상태 확인

```bash
systemctl status sendmail
systemctl status dovecot
```

## SMTP 연결 테스트

```bash
telnet mx1.hye12.local 25
```

## MX Record 조회

```bash
nslookup
```

```text
set type=mx
hye12.local
```
