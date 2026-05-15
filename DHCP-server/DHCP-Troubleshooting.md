# DHCP Troubleshooting

## DHCP Service Start Failure

### Problem

DHCP 서비스 실행 실패

```bash
systemctl enable --now dhcpd
```

```text
Job for dhcpd.service failed because the control process exited with error code.
```

## Log Check

```bash
journalctl -xe
```

## Error Message

```text
/etc/dhcp/dhcpd.conf line 14: semicolon expected.
/etc/dhcp/dhcpd.conf line 19: unexpected end of file
```

## Cause

- DHCP 설정파일(`dhcpd.conf`) 문법 오류 발생
- 세미콜론(`;`) 누락
- 중괄호(`{ }`) 설정 오류

## Solution

설정파일 수정 후 DHCP 서비스 재시작

```bash
vi /etc/dhcp/dhcpd.conf
```

```bash id="h0m8z7"
systemctl restart dhcpd
```
