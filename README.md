# PHPADMIN-ON-EC2
installation of oh-admin on ec2 (lamp server ,php admin)


sudo yum update -y
sudo amazon-linux-extras install -y lamp-mariadb10.2-php7.2 php7.2
sudo yum install -y httpd mariadb-server
sudo systemctl start httpd
sudo systemctl enable httpd
sudo systemctl is-enabled httpd
sudo usermod -a -G apache ec2-user
exit
groups
sudo chown -R ec2-user:apache /var/www
sudo chmod 2775 /var/www && find /var/www -type d -exec sudo chmod 2775 {} \;
find /var/www -type f -exec sudo chmod 0664 {} \;

sudo systemctl start mariadb
sudo mysql_secure_installation
sudo systemctl stop mariadb
sudo systemctl enable mariadb

sudo yum install php-mbstring -y
sudo systemctl restart httpd
sudo systemctl restart php-fpm
wget https://www.phpmyadmin.net/downloads/phpMyAdmin-latest-all-languages.tar.gz
mkdir phpMyAdmin && tar -xvzf phpMyAdmin-latest-all-languages.tar.gz -C phpMyAdmin --strip-components 1
rm phpMyAdmin-latest-all-languages.tar.gz

sudo service mysqld start   (if mysqld is configure, else      systemctl start mariadb)
http://my.public.dns.amazonaws.com/phpMyAdmin 
