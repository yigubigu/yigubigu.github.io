---
date: 2017-11-19 09:50:47+00:00
layout: post
title: 'mysql lock'
categories: 技术
tags:  mysql, lock
---

#1 Check Running Query

```
show engine innodb status;
```

#2 Show Process 

````
SHOW PROCESSLIST
````

#3 Show Open Tables
```
show open tables where In_Use > 0 ;
```

#4 Show Locks
```
SELECT 
    pl.id
    ,pl.user
    ,pl.state
    ,it.trx_id 
    ,it.trx_mysql_thread_id 
    ,it.trx_query AS query
    ,it.trx_id AS blocking_trx_id
    ,it.trx_mysql_thread_id AS blocking_thread
    ,it.trx_query AS blocking_query
FROM information_schema.processlist AS pl 
INNER JOIN information_schema.innodb_trx AS it
    ON pl.id = it.trx_mysql_thread_id
INNER JOIN information_schema.innodb_lock_waits AS ilw
    ON it.trx_id = ilw.requesting_trx_id 
        AND it.trx_id = ilw.blocking_trx_id

```