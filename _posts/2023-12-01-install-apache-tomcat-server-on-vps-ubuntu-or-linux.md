---
layout: post
title: Install Apache Tomcat Server on VPS Ubuntu or Linux
date: 2023-12-01 00:42 +0700
categories: [Deploy]
tags: [Apache Tomcat, VPS]
image:
  path: /assets/img/install-apache-tomcat-server-on-vps-ubuntu-or-linux/background.png
  width: 800
---

Step 1: Update APT

```shell
// First, as always, update your APT.
$ sudo apt update
```

Step 2: Install java

```shell
// Install jdk
$ apt install openjdk-11-jdk-headless
```

Step 3: Install Tomcat

```shell
// Check for Tomcat in Repository
$ sudo apt-cache search tomcat
// Download and install Tomcat
$ sudo apt install tomcat9 tomcat9-admin
// When the download is finished, it will install the Apache Tomcat Server, which will start up automatically. For verification, type the following ss command, which will show you the 8080 open port number, the default open port reserved for Apache Tomcat Server.
$ ss -ltn
// Change Tomcat Settings
$ sudo systemctl enable tomcat9
// Create User
$ sudo nano /etc/tomcat9/tomcat-users.xml
// Add Tagged Lines
<role rolename="manager-gui"/>
<role rolename="admin-gui"/>
<user username="{username}" password="{password}" roles="standard,admin-gui,manager-gui"/>
// Restart Tomcat
$ sudo systemctl restart tomcat9
// or sudo systemctl stop tomcat9 && sudo systemctl start tomcat9
```

Step 4: Install proxy

```shell
$ sudo apt-get install nginx
$ sudo systemctl stop nginx.service
$ sudo systemctl start nginx.service
$ sudo systemctl enable nginx.service
$ sudo nano /etc/nginx/sites-available/example


server {
	listen 80;
	listen [::]:80;
	server_name  public ip or domain name;



	proxy_redirect           off;
	proxy_set_header         X-Real-IP $remote_addr;
	proxy_set_header         X-Forwarded-For $proxy_add_x_forwarded_for;
	proxy_set_header         Host $http_host;

	location / {
			proxy_pass http://127.0.0.1:8080;
	}
}
$ sudo ln -s /etc/nginx/sites-available/example /etc/nginx/sites-enabled/
$ sudo systemctl restart nginx.service
```

Fix error: 413 Request Entity Too Large on Nginx

```shell
$ sudo nano /etc/nginx/nginx.conf

http {
    ...
    # Set value 'client_max_body_size'
    client_max_body_size 100M;
    ...
}

$ sudo nginx -s reload
```
