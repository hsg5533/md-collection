# Ubuntu 환경 설정 및 서버 구축 가이드

## 1. 오라클 버츄얼박스에서 우분투 설치
- '새로 만들기'를 눌러 가상머신을 생성 후, 가상머신을 켜고 우분투 ISO 파일을 삽입하여 설치
- 가상머신 생성 시 ISO를 미리 삽입하면 자동 설치되어 터미널 문제 발생 가능

## 2. Node.js 설치
```bash
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install curl
curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash --
sudo apt-get install nodejs
sudo npm install -g yarn
```

## 3. MySQL 8.0 설치
```bash
wget -c https://dev.mysql.com/get/mysql-apt-config_0.8.10-1_all.deb
sudo dpkg -i mysql-apt-config_0.8.10-1_all.deb
sudo apt update
sudo apt upgrade
sudo apt-get install mysql-server
```

## 4. MySQL Workbench 설치 및 연결
```bash
sudo snap install mysql-workbench-community
sudo snap connect mysql-workbench-community:password-manager-service :password-manager-service
```

### Access denied for user 'root'@'localhost' 에러 해결
```sql
sudo mysql -u root
use mysql;
select user,host,plugin from user;
update user set plugin='mysql_native_password' where user='root';
alter user 'root'@'localhost' identified with mysql_native_password BY '1234';
flush privileges;
select user,host,plugin from user;
exit;
```

## 5. 윈도우에서 우분투로 파일 전송
- `pscp` 명령어 사용: 
```bash
pscp [파일경로] root@[우분투IP]:[우분투경로]
```

## 6. iptables 명령어
```bash
iptables -A INPUT -d 139.150.83.6 -p tcp --dport 3030 -j DROP
```

## 7. Nginx 서버 설치 및 설정
```bash
sudo apt-get update
sudo apt install nginx
sudo vi /etc/nginx/sites-available/default
sudo ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/default
sudo systemctl stop nginx
sudo systemctl start nginx
sudo systemctl status nginx
sudo apt-get remove --purge nginx nginx-full nginx-common
```

## 8. Nginx HTTPS 적용
```bash
sudo apt-get install certbot python3-certbot-nginx
sudo certbot certonly --nginx -d [도메인]
```

### Nginx default 설정 예시
```nginx
server {
    listen 443;
    listen [::]:443;
    server_name app.tableon.co.kr;
    ssl on;
    ssl_certificate /etc/letsencrypt/live/app.tableon.co.kr/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/app.tableon.co.kr/privkey.pem;
    root /server/mp/build;
    index index.html index.htm index.nginx.debian.html;
    location / {
        try_files $uri $uri/ /index.html;
    }
}
server {
    listen 8080;
    listen [::]:8080;
    server_name app.tableon.co.kr;
    ssl on;
    ssl_certificate /etc/letsencrypt/live/app.tableon.co.kr/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/app.tableon.co.kr/privkey.pem;
    root /server/op/build;
    index index.html index.htm index.nginx.debian.html;
    location / {
        try_files $uri $uri/ /index.html;
    }
}
server {
    listen 80;
    listen [::]:80;
    server_name app.tableon.co.kr;
    return 301 https://$server_name$request_uri;
}
```

```bash
sudo systemctl restart nginx
```
