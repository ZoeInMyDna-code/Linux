2
# Server Provisioning and Apache Setup Documentation

## Overview
This repository contains the documentation of setting up my Linux server, installing Apache as the web server, deploying the HTML landing page about me, and configuring the server to allow HTTP traffic (port 80). Additionally, this README includes details about obtaining the public IP address, URL of the site, and any optional tasks completed (like setting up HTTPS).

## Server Provisioning
1. **Provision a Server:**
   - Server: Linux Server (Ubuntu 20.04)
   - Provider: AWS (Amazon Web Services)
   - Instance Type: t2.micro

2. **Connect to Server:**
   - SSH into the server using: `ssh -i pair.pem ubuntu@54.74.89.202`

3. **Update Package List and Install Apache:**
   ```bash
   sudo apt update
   sudo apt install apache2
   ```

4. **Verify Apache Installation:**
   ```bash
   sudo systemctl status apache2
   ```

## Web Server Installation (Apache)
1. **Install Apache:**
   - Apache is installed using the package manager.
   - Apache is used as the web server for serving HTML content.

2. **Start Apache Service:**
   ```bash
   sudo systemctl start apache2
   ```

3. **Enable Apache to Start on Boot:**
   ```bash
   sudo systemctl enable apache2
   ```

## HTML Page Deployment
1. **Create a Simple HTML Page:**
   - An HTML file named `index.html` was created in the `/var/www/html/` directory.
   - Content of `index.html` includes:
     - Name: Oluwatimileyin
     - Project Title: "Welcome to Oluwatimileyin Landing Page."
     - Brief description of the project.
     - Full bio with interesting information.

2. **Deploy HTML Page:**
   - The HTML file was deployed in the default Apache web directory `/var/www/html/`.
   - Access the page via URL: `http://54.74.89.202/   `

## Networking Configuration (Open Port 80)
1. **Configure Firewall to Allow HTTP Traffic (Port 80):**
   - Opened port 80 in the security group of my AWS EC2 instance.
   - In AWS, i went to **Security Groups**,I selected the security group for my server, and edit inbound rules to allow HTTP traffic (`Port 80`).

2. **Public IP Address or URL:**
   - Public IP Address: `http://54.74.89.202/`

## Optional Task: HTTPS Setup
SSL Configuration
To enable HTTPS, a self-signed SSL certificate was generated using OpenSSL. The certificate (/etc/ssl/certs/selfsigned.crt) and private key (/etc/ssl/private/selfsigned.key) were configured in Apache by modifying the default-ssl.conf file. While this certificate is not verified by a trusted Certificate Authority, it provides encryption for secure communication. I did a self-signed SSL certificate.

2. **Check HTTPS Connection:**
   -I Accessed my website via `https://54.74.89.202 ` to confirm the SSL certificate and HTTPS configuration.

## Conclusion
This GitHub repository documents the steps taken to provision a server, set up Apache, deploy the HTML page, configure networking for HTTP traffic, and implement an optional HTTPS setup with a Dynamic DNS subdomain for SSL certificate verification. All configurations were made to ensure the website can be accessed securely from the web.

## Additional Notes
- To access the website, use the URL: `http://54.74.89.202/`
- If HTTPS is configured, you can access via: `https://54.74.89.202/`.
- The server is configured for basic HTTP traffic, and for the optional task of setting up HTTPS, a free Dynamic DNS service was used.
