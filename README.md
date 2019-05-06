# wordpress-di-centos
make wordpress di centos didalam xenserver
## Update CentOS 7
```bash
yum clean all
yum update -y
```
## application needed
```bash
yum install wget curl nano -y
yum install epel-release -y
rpm -Uvh http://rpms.remirepo.net/enterprise/remi-release-7.rpm
```
## Install PHP
```bash
yum install php71-php php71-php-cli php71-php-common php71-php-json php71-php-intl php71-php-mbstring php71-php-mcrypt php71-php-mysqlnd php71-php-pdo php71-php-tidy php71-php-xml php71-php-fpm -y
```
## Install MySql
1. wget https://dev.mysql.com/get/mysql80-community-release-el7-1.noarch.rpm
2. sudo rpm -ivh mysql80-community-release-el7-1.noarch.rpm
3. sudo yum install MariaDB
make file at
'''bash
vi /etc/yum.repos.d/MariaDB.repo
'''
add this in file
'''bash
[mariadb]
name = MariaDB
baseurl = http://yum.mariadb.org/10.1/centos7-amd64
gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
gpgcheck=1
```
create mysql database and user for wordpress
```bash
// ** MySQL settings - You can get this info from your web host ** //
/** The name of the database for WordPress */
define('DB_NAME', 'database_name_here');
/** MySQL database username */
define('DB_USER', 'username_here');
/** MySQL database password */
define('DB_PASSWORD', 'password_here');
/** MySQL hostname */
define('DB_HOST', 'localhost');
```
## install nginx
```bash
sudo yum install epel-release yum-utils
sudo yum install http://rpms.remirepo.net/enterprise/remi-release-7.rpm
sudo yum-config-manager --enable remi-php72
sudo yum install php-cli php-fpm php-mysql php-json php-opcache php-mbstring php-xml php-gd php-curl
``` 
permissionn to folder root nginx
```bash
chown -R nginx:nginx /usr/share/nginx/wordpress.itzgeek.local/
```
editing wordpress conf.d/default.conf - nginx.conf
```bash
server {
    listen	 80;
    server_name  wordpressminion.com www.wordpressminion.com;

    #charset koi8-r;
    #access_log  /var/log/nginx/host.access.log  main;

    location / {
        root   /usr/share/nginx/html;
        index  index.html index.htm index.php;
    }

    #error_page  404              /404.html;

    # redirect server error pages to the static page /50x.html
    #
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
```
## Install WordPress
```bash
wget wordpress.org/latest.tar.gz 
tar zxvf latest.tar.gz
```
make directory for wordpress
 ```bash
mkdir /usr/share/nginx/wordpressminion.com
```
move file wordpress installer to /usr/share/nginx/wordpressminion.com
```bash
cp wordpress /usr/sharee/nginx/wordpressminion.com
```
## Test Wordpress
open browser IP http://"ip server"
