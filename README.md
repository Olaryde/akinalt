# Web Server Setup and Deployment  

This project demonstrates the process of provisioning a Linux server, setting up a web server, deploying a simple HTML landing page, and enabling HTTPS. It is designed to showcase basic cloud and web development skills.  

## Public IP Address  
Access the deployed web page at:  
**[https://18.133.33.124/](http://18.133.33.124/)**  

## Project Description  
This project involves 4 steps:  
1. Provisioning an EC2 instance on AWS with Ubuntu Linux.  
2. Installing and configuring the Nginx web server to serve an HTML page.  
3. Deploying an HTML landing page with a personal bio and project description.  
4. Configuring HTTPS using a free SSL certificate (Let’s Encrypt).  

## Steps to Reproduce  

### 1. Provision the Server  
1. Launch an EC2 instance on AWS using Ubuntu 20.04 LTS.  
2. Configure a Security Group to allow traffic on ports 22 (SSH) and 80 (HTTP).  
3. Connect to the instance via SSH using the provided public IP address.  

### 2. Install and Configure Nginx  
1. Update the package list:  
   ```bash
   sudo apt update
   ```  
2. Install Nginx:  
   ```bash
   sudo apt install nginx -y
   ```  
3. Start and enable the Nginx service:  
   ```bash
   sudo systemctl start nginx  
   sudo systemctl enable nginx  
   ```  

### 3. Deploy the HTML Page  
1. Navigate to the Nginx web root directory:  
   ```bash
   cd /var/www/html  
   ```  
2. Delete the default Nginx page:  
   ```bash
   sudo rm index.nginx-debian.html  
   ```  
3. Create a new `index.html` file with the following content:  
   ```html
       <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Akintunde Olaide Akinyemi</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
            margin: 20px;
            background-color: #f4f4f9;
            color: #333;
        }
        h1 {
            text-align: center;
            color: #444;
        }
        p {
            margin: 10px 0;
        }
    </style>
</head>
<body>
    <h1>Akintunde Olaide Akinyemi</h1>
    <p>My name is Akintunde Olaide Akinyemi. I am an accountant with 15 years of expert experience in the finance area. I graduated from Oxford Brookes University London and hold a Master's in Accountancy from the University of London.</p>
    <p>I have worked with AP Moller Maersk and am currently working with Tot. I have several achievements, which include the automation of invoice processing, the upgrade of financial statements to IFRS standards, among others.</p>
    <p>I started a course in Cloud Engineering with a passion for learning and as a way of contributing to society.</p>
</body>
</html>

   ```  
4. Restart Nginx:  
   ```bash
   sudo systemctl restart nginx  
   ```  

### 4. Configure HTTPS (Optional Bonus)  
1. Install OpenSSL: Use a self-signed SSL certificate (not trusted by browsers but works for testing  
   ```bash
   sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/nginx-selfsigned.key -out /etc/ssl/certs/nginx-selfsigned.crt  
   ```  
2. Configure Nginx to use the certificate::  
   ```bash
   sudo nano /etc/nginx/sites-available/default 
   ```  
3. Add the following under server { :
   ```bash
   listen 443 ssl;
   ssl_certificate /etc/ssl/certs/nginx-selfsigned.crt;
   ssl_certificate_key /etc/ssl/private/nginx-selfsigned.key;

4. Ensure port 443 is open in your AWS security group.

5. Restart Nginx server:
   ```bash
   sudo systemctl restart nginx

6. Access your site via https://13.41.189.61 (you’ll see a browser warning because it’s self-signed).


## Screenshot  
Include a screenshot of the landing page displayed in a browser.  

## Files Included  
- `index.html` – The HTML file deployed on the server.  
- Screenshot of the deployed web page.    
