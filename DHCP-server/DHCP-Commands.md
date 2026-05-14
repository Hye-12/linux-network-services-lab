# DHCP Commands

## DHCP Server 설치

```bash
dnf install -y dhcp-server
```

## DHCP 설정파일 수정
세부 설정: `DHCP-Server/dhcpd.conf`

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
