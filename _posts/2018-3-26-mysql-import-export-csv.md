
---
date: 2018-3-18 09:50:47+00:00
layout: post
title: 'Mysql CSV import and export'
categories: 技术
tags:  Mysql  
---

# Mysql Export/Import CSV

Export as CSV from mysql table using command line

Its similar to import first you have to login to mysql via CLI then choose the DB to connect with use command.

```

mysql --local-infile=1 -u root -p
//then it prompt for password. just type the password now you're in mysql cli.
use db_name
//select the database name you have to import the sheet
SELECT T.refference,T.name,T.price,T.tax,T.category FROM `product_temp` as T LEFT JOIN product_code as P ON P.reference = T.refference where P.reference is null INTO OUTFILE '/home/misseditem.csv' FIELDS TERMINATED BY ',' ENCLOSED BY '"' LINES TERMINATED BY '\n';
```


mport – Export Csv file using command line is simple and fast compare to browser UI. from phpmyadmin browser page when we upload some larger files with more data rows. it may not responding the browser and die the mysql server or apache server for few min.

CLI import or export is faster and easy methods. recently I have the same issue around 56K records of the product I need to import and export back in CSV format when I tried with phpmyadmin it didn’t work for me. So I tried with CLI it works quickly.

Import CSV file via command line in mysql

First you have to login to mysql with CLI.

```

mysql --local-infile=1 -u root -p
//then it prompt for password. just type the password now you're in mysql cli.
use db_name
//select the database name you have to import the sheet
load data local infile '/home/jobin/workspace/Product-Sheets-03-02-2016/ITEMLIST.csv' into table products
fields terminated by ','
enclosed by '"'
lines terminated by '\n';
```

only thing you have to make sure is your CSV columns and mysql table columns numbers and orders should matach exactly same other wise it may return error messages. yea its simple and only tooks less than 3 min for importing 56K rows.
