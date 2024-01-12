# Using Nginx as a Web Server

[Nginx](https://nginx.org) is a powerful, open-source web server and reverse proxy server. This guide will walk you through the steps to set up and use Nginx as a web server.

## Step 1: Install Nginx

### Ubuntu/Debian:

```bash
sudo apt update
sudo apt install nginx
CentOS/RHEL:
bash

sudo yum install epel-release
sudo yum install nginx
Step 2: Start and Enable Nginx
bash

sudo systemctl start nginx
sudo systemctl enable nginx
Step 3: Create Your Website Directory
bash

sudo mkdir -p /var/www/mywebsite
Step 4: Add Your Web Content
Add your website files to the directory you created. For example:

bash

sudo nano /var/www/mywebsite/index.html
Step 5: Configure Nginx
Edit the Nginx configuration file:

bash

sudo nano /etc/nginx/sites-available/mywebsite
Add the following configuration (replace yourdomain.com with your domain or IP address):

nginx

server {
    listen 80;
    server_name yourdomain.com www.yourdomain.com;

    root /var/www/mywebsite;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
Step 6: Create a Symbolic Link
bash

sudo ln -s /etc/nginx/sites-available/mywebsite /etc/nginx/sites-enabled
Step 7: Test Nginx Configuration
bash

sudo nginx -t
Step 8: Restart Nginx
bash

sudo systemctl restart nginx
Step 9: Adjust Firewall
If you have a firewall enabled, allow traffic on port 80:

bash

sudo ufw allow 80
Step 10: Access Your Website
Visit http://yourdomain.com in a web browser to see your Nginx-powered website.

Additional Tips:
SSL/TLS Configuration:
If you want to secure your website with SSL/TLS, obtain an SSL certificate and configure Nginx accordingly.

Logging:
Check Nginx access and error logs for troubleshooting or monitoring:

bash

sudo tail -f /var/log/nginx/access.log
sudo tail -f /var/log/nginx/error.log
Security:
Regularly update Nginx and configure security settings. Consider implementing best practices for securing your web server.
