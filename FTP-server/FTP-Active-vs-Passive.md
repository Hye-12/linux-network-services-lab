## Active Mode vs Passive Mode

FTP는 데이터 전송 방식에 따라 Active Mode와 Passive Mode로 구분된다.

### Active Mode

- 서버가 클라이언트에게 데이터 연결 요청
- 서버 측에서 클라이언트로 직접 접속
- 방화벽 환경에서 연결 실패 가능성 존재

```text
Client <--- Server Data Connection
```

### Passive Mode

- 클라이언트가 서버에 데이터 연결 요청
- 서버는 지정된 Passive Port 범위 사용
- NAT / 방화벽 환경에서 상대적으로 안정적

```text
Client ---> Server Data Connection
```

## Passive Mode 설정 이유

실습 환경은 VMware NAT 및 Windows Firewall 환경을 사용하므로
Passive Mode 설정을 적용하였다.

```conf
pasv_enable=YES
pasv_min_port=65000
pasv_max_port=65010
```

Passive Mode 사용 시 지정한 포트 범위를 방화벽에서 추가 허용해야 한다.

```bash
firewall-cmd --permanent --add-port=65000-65010/tcp
```
