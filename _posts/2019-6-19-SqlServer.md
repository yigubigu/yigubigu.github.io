---
date: 2019-6-19 18:50:47+00:00
layout: post
title: Sqlserver
categories: Database
tags:  sqlserver
---

# Restore 

SQLCMD -S localhost -U sa -P sa -Q "RESTORE DATABASE newDbName FROM disk='e:\sqlserver-backup\backupFileName.bak' WITH RECOVERY, MOVE 'OriginDbName' TO 'e:\sqlserver-data\newDbName.mdf', MOVE 'OriginDbName_Log' TO 'e:\sqlserver-data\newDbName.ldf'"
