---
date: 2019-4-14 18:50:47+00:00
layout: post
title: 'Tomcat'
categories: Tech
tags:  tomcat linux
---

# 1. Install for Single User

* Check if JAVA_HOME is already set 

````
echo $JAVA_HOME
````

If response is empty, then JAVA_HOME is not set.

* Set Variable

```
vi ~/.bashrc OR vi ~/.bash_profile
```

Add 
```
export JAVA_HOME=/usr/java/jre1.6.0_04
```
Save file

* Reload profile 

source ~/.bashrc OR source ~/.bash_profile



# 2 Create tomcat user

For security purposes, Tomcat should not be run under the root user. We will create a new system user and group with home directory /opt/tomcat that will run the Tomcat service:

```
sudo useradd -r -m -U -d /opt/tomcat -s /bin/false tomcat
```

# 3 Install Tomcat

Start by download the Tomcat archive in the /tmp directory using the following wget command:

```
wget http://www-eu.apache.org/dist/tomcat/tomcat-9/v9.0.14/bin/apache-tomcat-9.0.14.tar.gz -P /tmp
```

Once the download is completed, extract the Tomcat archive and move it to the /opt/tomcat directory:

```
sudo tar xf /tmp/apache-tomcat-9*.tar.gz -C /opt/tomcat
```
To have more control over Tomcat versions and updates, we will create a symbolic link latest which will point to the Tomcat installation directory:

```
sudo ln -s /opt/tomcat/apache-tomcat-9.0.14 /opt/tomcat/latest
```

The following command will change the directory ownership to user and group tomcat:


```
sudo chown -RH tomcat: /opt/tomcat/latest
```

The scripts inside bin directory must have executable flag:

sudo sh -c 'chmod +x /opt/tomcat/latest/bin/*.sh'

# 4 Create a systemd unit file
To run Tomcat as a service we will create a new unit file. Open your text editor and create a file named tomcat.service in the /etc/systemd/system/:

```
sudo nano /etc/systemd/system/tomcat.service
```
Paste the following configuration:

```
[Unit]
Description=Tomcat 9 servlet container
After=network.target

[Service]
Type=forking

User=tomcat
Group=tomcat

Environment="JAVA_OPTS=-Djava.security.egd=file:///dev/urandom -Djava.awt.headless=true"

Environment="CATALINA_BASE=/opt/tomcat/latest"
Environment="CATALINA_HOME=/opt/tomcat/latest"
Environment="CATALINA_PID=/opt/tomcat/latest/temp/tomcat.pid"
Environment="CATALINA_OPTS=-Xms512M -Xmx1024M -server -XX:+UseParallelGC"

ExecStart=/opt/tomcat/latest/bin/startup.sh
ExecStop=/opt/tomcat/latest/bin/shutdown.sh

[Install]
WantedBy=multi-user.target
```

Save and close the file and notify systemd that we created a new unit file:

```
sudo systemctl daemon-reload
```

Start the Tomcat service by executing:

```
sudo systemctl start tomcat
```

Check the service status with the following command:

```
sudo systemctl status tomcat
```

```
* tomcat.service - Tomcat 9 servlet container
   Loaded: loaded (/etc/systemd/system/tomcat.service; disabled; vendor preset: enabled)
   Active: active (running) since Wed 2018-09-05 15:45:28 PDT; 20s ago
  Process: 1582 ExecStart=/opt/tomcat/latest/bin/startup.sh (code=exited, status=0/SUCCESS)
 Main PID: 1604 (java)
    Tasks: 47 (limit: 2319)
   CGroup: /system.slice/tomcat.service
```

If there are no errors enable the Tomcat service to be automatically started at boot time:

```
sudo systemctl enable tomcat
```

# 5 Adjust the Firewall
If your server is protected by a firewall and you want to access Tomcat interface from the outside of your local network you need to open port 8080.

To allow traffic on port 8080 type the following command:

```
sudo ufw allow 8080/tcp
```
