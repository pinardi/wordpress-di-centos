# wordpress-di-centos
make wordpress di centos didalam xenserver

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



install nginx
'''bash
sudo yum install epel-release yum-utils
sudo yum install http://rpms.remirepo.net/enterprise/remi-release-7.rpm
sudo yum-config-manager --enable remi-php72
sudo yum install php-cli php-fpm php-mysql php-json php-opcache php-mbstring php-xml php-gd php-curl
``` 
