# HTTPD Commands

## Apache HTTP Server 설치

```bash
dnf install -y httpd
```

## HTTPD 설정파일 수정

```bash
vi /etc/httpd/conf/httpd.conf
```

## VirtualHost 설정파일 수정

```bash
vi /etc/httpd/conf.d/vir.conf
```

## 각 사이트별 index.html 파일 생성
```bash
mv /etc/httpd/conf.d/{welcome.conf,welcome.conf.bak}

mkdir /var/www/{html,blog,intra}
vi /var/www/html/index.html
vi /var/www/blog/index.html
vi /var/www/intra/index.html
```

## 설정 문법 검사

```bash
httpd -t
```

## HTTPD 서비스 실행

```bash
systemctl enable --now httpd
```

## 서비스 상태 확인

```bash
systemctl status httpd
```

## HTTPD 서비스 재시작

```bash
systemctl restart httpd
```

## Firewall Open

```bash
firewall-cmd --permanent --add-service=http
firewall-cmd --reload
```
