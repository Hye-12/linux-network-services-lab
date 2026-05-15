## 설정에 대한 설명

- `subnet 10.0.0.0 netmask 255.255.255.0`
  - DHCP 서비스를 제공할 네트워크 대역 설정

- `range 10.0.0.31 10.0.0.250`
  - 클라이언트에게 동적으로 할당할 IP 범위 지정

- `option domain-name-servers 10.0.0.12`
  - DHCP 클라이언트가 사용할 DNS 서버 주소 설정

- `option domain-name "hye12.local"`
  - 클라이언트에 적용할 도메인 이름 설정

- `option routers 10.0.0.254`
  - 기본 게이트웨이(라우터) 주소 설정

- `option broadcast-address 10.0.0.254`
  - 브로드캐스트 주소 설정 (현재 주석 처리 상태)

- `default-lease-time 3600`
  - 기본 IP 임대 시간 설정 (3600초)

- `max-lease-time 3600`
  - 최대 IP 임대 시간 설정 (3600초)

## Host 예약 설정 설명

- `host w10`
  - w10 장비에 대한 고정 IP 예약 설정

- `hardware ethernet 00:00:00:00:00:01`
  - 특정 장비의 MAC 주소 지정

- `fixed-address 10.0.0.101`
  - 해당 장비에 고정 IP 주소 할당

- `host w11`
  - w11 장비에 대한 고정 IP 예약 설정

- `fixed-address 10.0.0.201`
  - w11 장비에 고정 IP 주소 할당
