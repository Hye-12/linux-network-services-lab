# DHCP Troubleshooting

## DHCP Service Start Failure

### Problem

DHCP 서비스 실행 실패

```bash
systemctl enable --now dhcpd
```
```bash
subnet 10.0.0.0 netmask 255.255.255.0 {
  range 10.0.0.31 10.0.0.250;
  option domain-name-servers 10.0.0.12;
  option domain-name "hye12.local";
#  option routers 10.5.5.1;
  option broadcast-address 10.0.0.254;
  default-lease-time 3600;
  max-lease-time 3600;
}

host w10 {
  hardware ethernet 00:00:00:00:00:01;
  fixed-address 10.0.0.101
#임의로 ;을 제거해 트러블 슈팅 의도
}

host w11 {
  hardware ethernet 00:00:00:00:00:021;
  fixed-address 10.0.0.201;
}
```
```text
Job for dhcpd.service failed because the control process exited with error code.
```

## Log Check

```bash
journalctl -xe
```
```
░░ Defined-By: systemd
░░ Support: https://wiki.rockylinux.org/rocky/support
░░ 
░░ An ExecStart= process belonging to unit dhcpd.service has exited.
░░ 
░░ The process' exit code is 'exited' and its exit status is 1.
May 15 16:29:39 rocky9-3 systemd[1]: dhcpd.service: Failed with result 'exit-code'.
░░ Subject: Unit failed
░░ Defined-By: systemd
░░ Support: https://wiki.rockylinux.org/rocky/support
░░ 
░░ The unit dhcpd.service has entered the 'failed' state with result 'exit-code'.
May 15 16:29:39 rocky9-3 systemd[1]: Failed to start DHCPv4 Server Daemon.
░░ Subject: A start job for unit dhcpd.service has failed
░░ Defined-By: systemd
░░ Support: https://wiki.rockylinux.org/rocky/support
░░ 
░░ A start job for unit dhcpd.service has finished with a failure.
░░ 
░░ The job identifier is 908 and the job result is failed.
May 15 16:29:39 rocky9-3 dnf[1044]: Metadata cache refreshed recently.
May 15 16:29:39 rocky9-3 systemd[1]: dnf-makecache.service: Deactivated successfully.
░░ Subject: Unit succeeded
░░ Defined-By: systemd
░░ Support: https://wiki.rockylinux.org/rocky/support
░░ 
░░ The unit dnf-makecache.service has successfully entered the 'dead' state.
May 15 16:29:39 rocky9-3 systemd[1]: Finished dnf makecache.
░░ Subject: A start job for unit dnf-makecache.service has finished successfully
░░ Defined-By: systemd
░░ Support: https://wiki.rockylinux.org/rocky/support
░░ 
░░ A start job for unit dnf-makecache.service has finished successfully.
░░ 
░░ The job identifier is 822.

```

## Important Error Message

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
```
[root@rocky9-3 ~]# systemctl status dhcpd
● dhcpd.service - DHCPv4 Server Daemon
     Loaded: loaded (/usr/lib/systemd/system/dhcpd.service; enabled; preset: disabled)
     Active: active (running) since Fri 2026-05-15 16:31:25 KST; 7s ago
       Docs: man:dhcpd(8)
             man:dhcpd.conf(5)
   Main PID: 1075 (dhcpd)
     Status: "Dispatching packets..."
      Tasks: 1 (limit: 12120)
     Memory: 5.1M
        CPU: 7ms
     CGroup: /system.slice/dhcpd.service
             └─1075 /usr/sbin/dhcpd -f -cf /etc/dhcp/dhcpd.conf -user dhcpd -group dhcpd --no-pid

May 15 16:31:25 rocky9-3 dhcpd[1075]: PID file: /var/run/dhcpd.pid
May 15 16:31:25 rocky9-3 dhcpd[1075]: Source compiled to use binary-leases
May 15 16:31:25 rocky9-3 dhcpd[1075]: Wrote 0 deleted host decls to leases file.
May 15 16:31:25 rocky9-3 dhcpd[1075]: Wrote 0 new dynamic host decls to leases file.
May 15 16:31:25 rocky9-3 dhcpd[1075]: Wrote 1 leases to leases file.
May 15 16:31:25 rocky9-3 dhcpd[1075]: Listening on LPF/ens160/00:0c:29:9c:b0:9a/10.0.0.0/24
May 15 16:31:25 rocky9-3 dhcpd[1075]: Sending on   LPF/ens160/00:0c:29:9c:b0:9a/10.0.0.0/24
May 15 16:31:25 rocky9-3 dhcpd[1075]: Sending on   Socket/fallback/fallback-net
May 15 16:31:25 rocky9-3 dhcpd[1075]: Server starting service.
May 15 16:31:25 rocky9-3 systemd[1]: Started DHCPv4 Server Daemon.
```
