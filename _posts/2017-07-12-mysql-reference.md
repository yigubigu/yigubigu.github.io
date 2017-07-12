

#1 Security
##1.1 Set Password
 SET PASSWORD FOR 'root'@'localhost' = PASSWORD('root');

##1.2 Safe Update
SET SQL_SAFE_UPDATES = 0;

#2 JDBc
##2.1 Driver Name  
com.mysql.jdbc.Driver
##2.2 Url
jdbc:mysql://localhost:3306/wso2?useUnicode=true&characterEncoding=utf8

#3 Database Operation
##3.1 Create Database
CREATE DATABASE `wordpress` DEFAULT CHARACTER SET utf8 COLLATE utf8_general_ci
##3.2 Create User
CREATE USER 'sonar'@'localhost' IDENTIFIED BY 'sonar';
CREATE USER 'jiqiren'@'%' IDENTIFIED BY 'jiqiren';
Note: '%' means any machine;

##3.3 Grant User Permission
GRANT ALL ON sonar.* TO 'sonar'@'%';
Note: '%' means any machine

##3.4 Backup
mysqldump -u root -p[root_password] [database_name] > dumpfilename.sql
##3.5 Restore
mysql -u root -p[root_password] [database_name] < dumpfilename.sql
