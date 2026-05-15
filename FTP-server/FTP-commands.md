# FTP Commands

## VSFTPD 설치

```bash
dnf install -y vsftpd
```

## VSFTPD 설정파일 수정

```bash id="0hx9q6"
vi /etc/vsftpd/vsftpd.conf
```

## VSFTPD 서비스 실행

```bash id="97wkg8"
systemctl enable --now vsftpd
```

## 서비스 상태 확인

```bash id="m0whb0"
systemctl status vsftpd
```

## 로그 확인

```bash id="2gth5s"
journalctl -xeu vsftpd
```

## Firewall Open

```bash id="lccjja"
firewall-cmd --permanent --add-service=ftp
firewall-cmd --reload
```
