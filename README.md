# deployed-wordpress-website

0.  initially connect EC2 with your local through command 

     ssh -i /Users/adarsh/Downloads/jenkinsKVP.pem ubuntu@34.206.233.22

1. Install Apache server on Ubuntu
sudo apt install apache2

2. Install php runtime and php mysql connector
sudo apt install php libapache2-mod-php php-mysql

3. Install MySQL server
sudo apt install mysql-server 

4. Login to MySQL server
sudo mysql -u root

5. Change authentication plugin to mysql_native_password (change the password to something strong)
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by 'Anypassword';

6. Create a new database user for wordpress (change the password to something strong)
CREATE USER 'wp_user'@localhost IDENTIFIED BY 'Anypassword';

7. Create a database for wordpress
CREATE DATABASE wp;

8. Grant all privilges on the database 'wp' to the newly created user
GRANT ALL PRIVILEGES ON wp.* TO 'wp_user'@localhost;

9. Download wordpress
cd /tmp
wget https://wordpress.org/wordpress-6.6.1.tar.gz

10. Unzip
tar -xvf wordpress-6.6.1.tar.gz

11. Move wordpress folder to apache document root
sudo mv wordpress/ /var/www/html

12. Command to restart/reload apache server
sudo systemctl restart apache2
OR
sudo systemctl reload apache2

congratulations on deploying your wordpress website ..
