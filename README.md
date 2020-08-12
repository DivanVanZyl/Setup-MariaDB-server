# Setup-MariaDB-server
Setup MariaDB server for remote client access

The option file in the home dir had no effect.
Option file that actually registed with MariaDB: /etc/mysql/my.cnf

Comment out the below lines:
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
