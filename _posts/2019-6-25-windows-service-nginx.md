---
date: 2019-6-19 18:50:47+00:00
layout: post
title: Windows Service Nginx
categories: nginx
tags:  nginx
---

# Nginx Windows Service 

## Copy Files To Local
nginx-1.15.8.zip
nssm-2.24.zip

## Unzip Files
unzip  nginx-1.15.8.zip and nssm-2.24.zip

## Config nginx
%nginx_home%\conf\nginx.conf

### Config port

```
Port 12345
```
### Config File Folder 

```

location /bw {
            alias   C:\\tibco\\tra\\domain\\WynnQAWP\\application\\logs;
			autoindex on;
            index  index.html index.htm;
}
location /offline {
            alias   C:\\var\\log\\wynn;
			autoindex on;
            index  index.html index.htm;
 }
```

### Example

```
server {
        listen       12345;
        server_name  localhost;

        #charset koi8-r;

        #access_log  logs/host.access.log  main;
  location / {
            root   html;
            autoindex on;
            index  index.html index.htm;
        }
        location /bw {
            location ~.log {
				add_header Content-Type text/plain;
			}
            alias   C:\\tibco\\tra\\domain\\WynnQAWP\\application\\logs;
			autoindex on;
            index  index.html index.htm;
        }
		location /offline {
            alias   C:\\var\\log\\wynn;
			autoindex on;
            index  index.html index.htm;
        }
```

## Install Nginx as Windows Service

- 1. Go to ommand line, run  "nssm.exe install nginx"
- 2. In NSSM gui do the following:
- 3. On the application tab: set path to C:\mysoftware\nginx-1.15.8\nginx.exe, set startup directory to C:\mysoftware\nginx-1.15.8
- 4. On the I/O tab type "start nginx" on the Input slow. Optionally set C:\mysoftware\nginx-1.15.8\logs\service.out.log and C:\mysoftware\nginx-1.15.8\logs\service.err.log in the output and error slots
- 5. Click "install service". Go to services, start "nginx"
- 6. Open http://localhost:12345 in chrome





