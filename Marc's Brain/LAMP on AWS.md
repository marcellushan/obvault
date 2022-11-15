
* Update OS
   * sudo yum update -y
* Install the lamp-mariadb10.2-php7.2 and php7.2 Amazon Linux Extras repositories
   * sudo amazon-linux-extras install -y lamp-mariadb10.2-php7.2 php7.2        
* Install the Apache web server, MariaDB, and PHP software packages
   * sudo yum install -y httpd mariadb-server
* Start the web server
   * sudo systemctl start httpd
* Set web server to start automatically each boot
   * sudo systemctl enable httpd
* Add ec2-user to the apache group
   * sudo usermod -a -G apache ec2-user
* Logout and back in as ec2-user
* Change the group ownership of /var/www and its contents to the apache group
   * sudo chown -R ec2-user:apache /var/www
* To add group write permissions and to set the group ID on future subdirectories, change the directory permissions of /var/www and its subdirectories.
   * sudo chmod 2775 /var/www && find /var/www -type d -exec sudo chmod 2775 {} \;
* To add group write permissions, recursively change the file permissions of /var/www and its subdirectories:
   * find /var/www -type f -exec sudo chmod 0664 {} \;
* Test LAMP server
   * echo "<?php phpinfo(); ?>" > /var/www/html/phpinfo.php
* Secure Database server
   * Start DB Server
      * sudo systemctl start mariadb
   * Auto-start mariadb
      * sudo systemctl enable mariadb
   * Run mysql_secure_installation
      * sudo mysql_secure_installation        
* Set db to start automatically
   *