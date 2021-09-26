Linux
Apache
MariaDB
PHP

* Install

** Install firewall

sudo yum install firewalld
sudo service firewalld start
sudo systemctl enable firewalld

** Install httpd / configure / firewall / start
sudo yum install -y httpd php php-mysql
sudo firewall-cmd --permanent --zone=public --add-port=80/tcp
sudo firewall-cmd --reload

sudo vi /etc/httpd/conf/httpd.conf #
# configure DirectoryIndex to use index.php instead of index.html


sudo service httpd start
sudo systemctl enable httpd

sudo yum install -y git
git clone https://github.com/<app>.git /var/www/html/
# update configure to user right database and so on

curl http://localhost

** Install mariaDB / configure / start / firewall / database / load data

sudo yum install mariadb-server
sudo vi /etc/my.cnf # configure
sudo service mariadb start
sudo systemctl enable mariadb
sudo firewall-cmd --permanent --zone=public --add-port=3306/tcp
sudo firewall-cmd --reload

mysql
  CREATE DATABASE ecomdb;
  CREATE USER 'ecomuser'@'localhost' INDENTIIFIED BY 'ecompassword';
  GRANT ALL PRIVILEGES ON *.* TO 'ecomuser'@'localhost'
  FLUSH PRIVILEGES;
mysql < db-load-script.sql

** Install PHP / download code / Test
