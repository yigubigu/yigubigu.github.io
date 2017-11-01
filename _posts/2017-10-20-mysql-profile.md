---
date: 2017-09-28 09:50:47+00:00
layout: post
title: 'mysql profile'
categories: 文档
tags:  mysql, profile
---

#1 Use Profile
```
select @@have_profling;

set profiling = 1;

select * from shipment;
show profiles;
show profile for query 2;

set @query_id := 2;

set @query_id := 2;
 
select state, sum(duration) as total_r, round( 100 * sum(duration) / (select sum(duration) from information_schema.profiling where query_id = @query_id), 2) as pct_r,
      count(*) as calls,
      sum(duration) / count(*) as 'r/call'
      from information_schema.profiling
      where query_id = @query_id
      group by state
      order by total_r desc;

show profile source for query 2;      

```

#2 Use Trce

set optimizer_trace="enabled=on", end_markers_in_json=on;

set optimizer_trace_max_mem_size=100000;

select * from xxxtxxxx where enterprise_code = 'E0000001' and created_date between '2017-10-16 00:00:00' and '2017-10-16 11:59:00';

select * from information_schema.optimizer_trace;

#3 定期分析表

anaylize table abc;
check table abc;

优化表
optimize table  abc;

#4 innodb_file_per_table

