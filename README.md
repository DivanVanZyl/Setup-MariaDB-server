# Setup-MariaDB-server
Setup MariaDB server for remote client access

Installed on Ubuntu 20:
sudo apt install mariadb-server

Edit the option file.
The option file in the home dir had no effect in my case.
Option file that actually registed with MariaDB:
sudo nano /etc/mysql/my.cnf

Comment out the below lines(if exists):
 [mysqld]
    ...
    #skip-networking
    ...
    #bind-address = <some ip-address>
    ...
    
Append the end like this:
[mysqld]
skip-networking=0
skip-bind-address

To restart and apply config changes:sudo systemctl restart mariadb

Log into mysql command line client with: sudo mysql

Set up user with remote access:
grant all privileges on *.* to 'root'@'DESKTOP-1234.home' identified by 'SomePassword' with grant option;

Check users:
sleect user, host from sqlserver.user;

Install firewalld:
sudo apt install firewalld

Add exception to firewall for port 3306:
sudo firewall-cmd --add-port=3306/tcp
sudo firewall-cmd --permanent --add-port=3306/tcp
