# HTTPD Overview

## HTTPD란?

HTTPD는 Apache HTTP Server 서비스로, 웹 페이지를 제공하는 웹 서버이다.

---

## 실습 목적

- Apache HTTP Server 설치
- VirtualHost 설정
- 도메인별 웹 페이지 분리
- Directory 접근제어 설정
- Basic Authentication 설정
- DNS와 웹 서버 연동 확인

---

## 실습 도메인

| Domain | DocumentRoot | Purpose |
|---|---|---|
| hye12.local | /var/www/html | Main Web Server |
| www.hye12.local | /var/www/html | Main Web Server Alias |
| blog.hye12.local | /var/www/blog | Blog Server |
| intra.hye12.local | /var/www/intra | Intra Server |

---

## 주요 설정 내용

- `VirtualHost`를 이용해 도메인별 웹 페이지 분리
- `ServerAlias`를 이용해 `www.hye12.local` 연결
- `/var/www/blog` 디렉토리에 IP 기반 접근제어 적용
- `/var/www/intra` 디렉토리에 사용자 인증 적용

---

## 테스트 내용

- 브라우저에서 각 도메인 접속 확인
- blog 페이지 접근제어 확인
- intra 페이지 Basic Authentication 확인
- `systemctl status httpd`로 서비스 상태 확인
