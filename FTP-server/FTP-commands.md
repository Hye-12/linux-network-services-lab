# FTP Commands

## VSFTPD 설치

```bash
dnf install -y vsftpd
```

## VSFTPD 설정파일 수정

```bash id="0hx9q6"
vi /etc/vsftpd/vsftpd.conf
```
## 전체 세부설정파일 `/FTP-server/FTP-config.conf`
```conf
## VSFTPD 추가 설정

xferlog_file=/ftp/xferlog       # FTP 업로드 및 다운로드 로그 저장 위치 설정
idle_session_timeout=600        # 일정 시간(600초) 동안 작업이 없을 경우 세션 종료
data_connection_timeout=120     # 데이터 연결 시간 초과 설정

banner_file=/ftp/ban            # FTP 접속 시 출력할 배너 파일 지정

chroot_list_enable=YES          # 특정 사용자에 대해 chroot 기능 사용
chroot_list_file=/ftp/ch        # chroot 적용 사용자 목록 파일 지정

allow_writeable_chroot=YES      # chroot 환경에서 쓰기 권한 허용

pasv_enable=YES                 # Passive Mode 사용 활성화
pasv_min_port=65000             # Passive Mode 최소 포트 지정
pasv_max_port=65010             # Passive Mode 최대 포트 지정

deny_file={*.exe}               # .exe 파일 업로드 제한
```
## `/ftp/ban` ftp banner 파일내용
```
=====================================
        HYE12 FTP SERVER
=====================================

WARNING

Authorized Access Only
All activities are monitored and logged.
Unauthorized access is prohibited.
```

## `/ftp/ch` chroot_list 파일
```
hye1
hye2
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
firewall-cmd --permanent --add-port=65000-65010/tcp
firewall-cmd --reload
```
