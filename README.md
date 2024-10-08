# EC2 Instance Setup and Website Deployment Guide

This guide provides detailed instructions on how to launch and configure an Amazon EC2 instance, install a web server, and deploy a website. Follow the steps below to get your EC2 instance up and running.

## Prerequisites

- Amazon AWS account with access to EC2 services
- Basic knowledge of Linux commands
- SSH client (e.g., terminal, Putty)

---

## Steps to Launch an EC2 Instance

### 1. Log in as a Root User

- Open the AWS Management Console and log in using your root user credentials.

### 2. Search for EC2

- In the search bar at the top of the console, type `EC2` and select it from the dropdown.

### 3. Create an EC2 Instance

- Click on the "Launch Instance" button.
- **Instance Name**: Give a unique name to your EC2 instance (e.g., `MyWebServer`).
- **Instance Type**: Select the type of instance, such as `Amazon Linux` or `Ubuntu`.

### 4. Configure Key Pair

- Create a new key pair to securely connect to your instance, and download it to your local machine.

### 5. Launch the Instance

- Click on the **Launch Instance** button to start your EC2 instance.

### 6. Connect to EC2 Instance

- Once your instance is running, go to the **EC2 Instances Dashboard**.
- Select your instance and click the **Connect** button.
- Choose **EC2 Instance Connect** to securely access your instance.

---

## Web Server Setup (Terminal Commands)

After connecting to your EC2 instance, follow these commands to set up and configure a web server.

1. **Switch to Root User:**
   ```bash
   sudo su -
   ```
2. **Update System Packages::**
   yum update -y

3. **Install Apache Web Server (httpd)::**
   yum install -y httpd
4. **Check the Status of the Web Server:**
   systemctl status httpd
5. **Create a Temporary Directory and Navigate Into It:**
   mkdir temp && cd temp
6. **Download a Website Template:**
   wget https://www.free-css.com/assets/files/free-css-templates/download/page296/listrace.zip

7. **Verify the Download:**
   ls -lrt
8. **unzip listrace.zip**
   unzip listrace.zip
9. **List the Files and Folders After Unzipping:**
   ls -lrt
10. **Navigate to the Unzipped Folder:**
    cd [folderWithoutZip]
11. **List Contents Inside the Folder:**
    ls -lrt
12. **Move Website Files to Apache's Root Directory (/var/www/html):**
    mv \* /var/www/html/

13. **Navigate to /var/www/html/:**
    cd /var/www/html/
14. **List Files in the Apache Web Directory:**
    ls -lrt

**Security Group Configuration**

15. **Allow HTTP/HTTPS Traffic**
    Go to the Security Groups tab of your EC2 instance.
    Add rules to allow inbound HTTP and HTTPS traffic.

**Final Steps: Start and Enable the Web Server 16.** 16. **Check Web Server Status:**
systemctl status httpd 17. **Enable Apache to Start on Boot:**
systemctl enable httpd

18. **Start the Apache Web Server:**
    systemctl start httpd

19. **Verify Web Server Status:**
    systemctl status httpd

20. **Troubleshooting**
    If you encounter issues accessing your website via the public IP address, ensure that:

Security group rules are correctly set up to allow HTTP/HTTPS traffic.
The Apache server is running (systemctl start httpd).
Accessing Your Website
Once the above steps are completed, you should be able to access your website by visiting the public IP address of your EC2 instance in a browser.

21. **http://<Your_Public_IP>**
    License
    This project is open-source and available under the MIT License.

This README is structured for GitHub documentation with appropriate Markdown formatting for headings, code blocks, and instructions. It covers the full process from launching an EC2 instance to deploying a web server and setting up a website.
