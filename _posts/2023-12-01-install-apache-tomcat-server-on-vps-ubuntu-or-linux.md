---
layout: post
title: 🛠 Install Apache Tomcat Server on VPS Ubuntu or Linux
date: 2023-12-01 00:42 +0700
categories: [DevOps]
tags: [Apache Tomcat, VPS]
image:
  path: /assets/img/install-apache-tomcat-server-on-vps-ubuntu-or-linux/background.png
  width: 800
---
## 📌 Step 1: Update APT

```sh
# First, always update your APT package list.
sudo apt update
```

---

## ☕ Step 2: Install Java

```sh
# Install OpenJDK 11 (Required for Tomcat)
sudo apt install openjdk-11-jdk-headless
```

---

## 🔥 Step 3: Install Apache Tomcat

```sh
# Check for Tomcat in the repository
sudo apt-cache search tomcat

# Download and install Tomcat
sudo apt install tomcat9 tomcat9-admin

# Verify Tomcat is running on port 8080
ss -ltn

# Enable Tomcat service to start on boot
sudo systemctl enable tomcat9

# Create a Tomcat user
sudo nano /etc/tomcat9/tomcat-users.xml
```

📌 **Add the following lines in `tomcat-users.xml`:**

```xml
<role rolename="manager-gui"/>
<role rolename="admin-gui"/>
<user username="{username}" password="{password}" roles="standard,admin-gui,manager-gui"/>
```

```sh
# Restart Tomcat to apply changes
sudo systemctl restart tomcat9

# Alternative way to restart Tomcat
sudo systemctl stop tomcat9 && sudo systemctl start tomcat9
```

---

## 🌍 Step 4: Install and Configure Nginx as a Reverse Proxy

```sh
# Install Nginx
sudo apt-get install nginx

# Start and enable Nginx service
sudo systemctl stop nginx.service
sudo systemctl start nginx.service
sudo systemctl enable nginx.service

# Configure Nginx proxy settings
sudo nano /etc/nginx/sites-available/example
```

📌 **Add the following configuration:**

```nginx
server {
    listen 80;
    listen [::]:80;
    server_name public_ip_or_domain_name;

    proxy_redirect off;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header Host $http_host;

    location / {
        proxy_pass http://127.0.0.1:8080;
    }
}
```

```sh
# Enable the Nginx configuration
sudo ln -s /etc/nginx/sites-available/example /etc/nginx/sites-enabled/

# Restart Nginx service to apply changes
sudo systemctl restart nginx.service
```

---

## ❗ Fix Error: **413 Request Entity Too Large on Nginx**

```sh
# Open Nginx config file
sudo nano /etc/nginx/nginx.conf
```

📌 **Add or update the following line inside the `http {}` block:**

```nginx
http {
    ...
    # Allow larger file uploads
    client_max_body_size 100M;
    ...
}
```

```sh
# Reload Nginx configuration
sudo nginx -s reload
```

---

## 🎯 Conclusion

✔️ **Tomcat 9 is successfully installed and running on your Ubuntu/Linux VPS!**  
✔️ **Nginx is configured as a reverse proxy for better security and performance.**  
✔️ **Now, your Tomcat server is accessible via your domain or public IP!** 🚀