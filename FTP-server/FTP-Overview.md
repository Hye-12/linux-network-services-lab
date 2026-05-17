# FTP Overview

## FTP란?

FTP(File Transfer Protocol)는 파일 전송을 위한 프로토콜이다.

기본적으로:
- 21번 포트 : 제어 연결(Control Connection)
- 20번 포트 : 데이터 연결(Data Connection)

을 사용한다.

---

## 실습 목적

- VSFTPD 설치 및 설정
- FTP 사용자 접속 테스트
- Passive Mode 구성
- 방화벽 및 포트 설정
- FileZilla를 통한 접속 확인

---

## 실습 환경

- Rocky Linux 9
- Windows 10
- VMware Workstation

---

## 주요 설정

- Local User Login
- Chroot 제한
- Passive Mode
- FTP Banner 설정
- Upload 제한 설정

---

## 테스트 내용

- CMD FTP 접속
- FileZilla 접속
- Passive Port 동작 확인
- 로그 기록 확인
