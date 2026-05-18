# Linux Network Services Lab
Rocky Linux 기반 네트워크 서비스 구축 실습 저장소

## Labs
- DHCP Server (10.0.0.13)
- FTP Server  (10.0.0.11)
- DNS Server
  - Primary DNS : 10.0.0.12
  - Secondary DNS : 10.0.0.11
  - Secondary DNS : 10.0.0.13

## Lab Topology
| Host | rocky9-1 | rocky9-2 | rocky9-3 | rocky9-4 | W10 | W11 |
|---|---|---|---|---|---|---|
| Role | Secondary DNS | Primary DNS | Secondary DNS<br>DHCP Server | Database Server | Windows Client | Windows Client |
| IP | 10.0.0.11 | 10.0.0.12 | 10.0.0.13 | 10.0.0.14 | 10.0.0.101 | 10.0.0.201 |
| Domain | hye12.local<br>www.hye12.local<br>blog.hye12.local<br>ftp.hye12.local | hye12.local<br>www.hye12.local<br>blog.hye12.local<br>intra.hye12.local | hye12.local<br>www.hye12.local<br>intra.hye12.local<br>mx1.hye12.local | mysql.hye12.local | DHCP/DNS Client | DHCP/DNS Client |
| Service | FTP<br>Blog Web | DNS Master<br>Main/Intra Web | DHCP<br>Mail | MySQL | Test | Test |

## Environment
- Rocky Linux 9
- Windows 10/11
- VMware Workstation
