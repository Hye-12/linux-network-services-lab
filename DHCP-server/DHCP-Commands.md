# DHCP Commands

## DHCP Server 설치

```bash
dnf install -y dhcp-server
```

## DHCP 설정파일 수정
세부 설정: `DHCP-Server/dhcpd.conf`
`/usr/share/doc/dhcp-server/dhcpd.conf.example` 의 기초 내용을 복사 후 수정 필요
':$r /usr/share/doc/dhcp-server/dhcpd.conf.example' 명령문으로 샘플내용 복사 후 수정 진행


```bash
vi /etc/dhcp/dhcpd.conf
```

## DHCP Server 실행

```bash
systemctl enable --now dhcpd
```

## Log 확인 필요 시

```bash
journalctl -xeu dhcpd
```

## Firewall Open

```bash
firewall-cmd --permanent --add-service=dhcp
firewall-cmd --reload
```
