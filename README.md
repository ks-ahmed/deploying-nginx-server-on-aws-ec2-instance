# Nginx on AWS EC2 with DNS routing using Cloudflare.


This project demonstrates designing and deploying of a real-world networked web-app by deploying an NGINX web server on an Amazon Web Service (AWS) EC2 instance and making it accessible via a custom domain using Cloudflare DNS.

---

## Overview

- Designing and deploying cloud-based network infrastructure.
- Understanding the core components of web traffic, server configuration, and DNS.
- Registering and configuring a custom domain with proper DNS records.

---

## Network Overview

| Concept                        | Description                                                                                                         |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------- |
| **IP Addressing & Subnetting** | Decoding the differences between public and private IPs, and applying subnetting principles and routing logic.       |
| **DNS**                        | Investigating how domain names are resolved, DNS record types, and configuring domain routing.                           |
| **Routing & Firewalls**        | Setting up AWS security groups and managing routing for secure and correct network traffic flow.                    |
| **Web Server Deployment**      | Installing and configuring NGINX to serve HTTP content on a live server.                                            |
| **Cloud Infrastructure**       | Creating and managing EC2 instances on AWS to host web services.                                                    |
| **Domain Management**          | Purchasing a domain and configuring DNS settings via Cloudflare.                                                    |
| **Network Security**           | Implementing firewall rules and access controls to protect server resources.                                        |


---

## Project Steps

### 1. Domain Purchase
- Acquired a custom domain from **Cloudflare**.

  ![Screenshot from 2025-05-18 13-32-32](https://github.com/user-attachments/assets/9364f4d3-265d-48b4-8ac1-02de61b3a342)

---

- Managed DNS settings via Cloudflare dashboard by configuring **DNS A record** to point to my EC2 instance.

![Screenshot 2025-05-19 172112](https://github.com/user-attachments/assets/5ca4e8b0-f715-45e9-86a3-0e7a10173f42)

---

### 2. EC2 Instance Setup
- Launched a **t3.micro** Amazon EC2 instance using **Ubuntu**.

  ![Screenshot from 2025-05-18 19-06-42](https://github.com/user-attachments/assets/ddcb7b67-1628-4271-aa1f-bceae607ae9d)

  ---

- Configured inbound rules to allow **HTTP (port 80)** traffic.

  ![Screenshot 2025-05-19 171733](https://github.com/user-attachments/assets/96e797ca-b42c-41f2-9e50-98fd130406f6)

---

### 3. Install NGINX
- Connected to the EC2 instance via SSH.

![Screenshot from 2025-05-18 19-08-54](https://github.com/user-attachments/assets/68097f4b-48a0-4327-8ec5-45223023a209)

---

- Installed NGINX using:
  
  `sudo apt update`
  `sudo apt install nginx -y`
  

  ![Screenshot from 2025-05-18 19-15-53](https://github.com/user-attachments/assets/521e7ec5-e32b-482c-b27e-c8f906404c64)

---

Verified the service was running using:

`sudo systemctl status nginx`


![Screenshot from 2025-05-19 13-38-49](https://github.com/user-attachments/assets/e8e54e69-d47e-48f9-9403-d6b63526d652)


---

### 4. Domain-to-IP Mapping

| Configuration Step   | Details                                                              |
| -------------------- | -------------------------------------------------------------------- |
| **DNS Provider**     | Cloudflare                                                           |
| **Record Type**      | A (Address) Record                                                   |
| **Host**             | `nginx.vettlyai.com`                                                 |
| **Value**            | Public IP address of the EC2 instance                                |
| **Propagation Time** | \~5–10 minutes for DNS changes to take effect globally               |
| **Result**           | Domain successfully routed to the NGINX web server hosted on AWS EC2 |


![Screenshot from 2025-05-19 16-13-10](https://github.com/user-attachments/assets/cb8282c9-3cae-4314-a57d-0bababa1962c)


---

### 5. 5. Custom Homepage 

To go beyond and demonstrate a curious thought, I verified public accessibility through the NGINX landing page via the domain and mapped custom domain `nginx.vettlyai.com` to the EC2 instance. 

| Element                 | Description                                                                                                                                                                                          |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------
| **File Edited**         | `/var/www/html/index.html`                                                                                                                                                                           |
| **Command Used**        | `sudo /var/www/html/index.html`                                                                                                                                                               
| **Customization Goals** | - Replaced default NGINX landing page<br>- Added branding for `nginx.vettlyai.com`<br>- Wrote a welcome message explaining the project<br>- Used                             simple, semantic HTML and light styling for clarity |
| **Purpose**             | Enhance the user experience, present the project professionally, and demonstrate attention to detail.                                                                                            

![image1](https://github.com/user-attachments/assets/fa8da1d6-d224-4e26-a973-2958c09da8d1)


![Screenshot from 2025-05-19 18-34-49](https://github.com/user-attachments/assets/e552d8d7-38f8-4b56-9a9b-4db5a003ceb5)


---

### ⚙️ Tools & Technologies

| Tool / Technology             | Purpose                                                                   |
| ----------------------------- | ------------------------------------------------------------------------- |
| **Amazon Web Services (EC2)** | Hosting a virtual server to deploy the NGINX web server.                  |
| **NGINX Web Server**          | Serving web content over HTTP; handling incoming web requests.            |
| **Cloudflare DNS**            | Managing the domain name and routing traffic to the EC2 instance.         |
| **Ubuntu Linux**              | Operating system environment for configuring and running the server.      |
| **Bash / Terminal**           | Executing server commands, software installation, and file configuration. |
| **SSH**                       | Securely connecting to and managing the remote EC2 instance.              |
| **HTML**                      | Customizing the default NGINX homepage with structured, styled content.   |


---

### Troubleshooting (DNS Lookups)

Used command-line tools to verify DNS configuration and ensure the domain correctly pointed to the EC2 instance.

| Tool           | Purpose                                                                                 |
| -------------- | --------------------------------------------------------------------------------------- |
| **`dig`**      | Queried DNS records to confirm that `nginx.vettlyai.com` resolved to the EC2 public IP. |
| **`nslookup`** | Verified the domain-to-IP resolution and checked authoritative DNS response.            |


### Command UsedL
`dig nginx.vettlyai.com` and
`nslookup nginx.vettlyai.com`

![Screenshot from 2025-05-19 13-39-09](https://github.com/user-attachments/assets/458e80aa-4540-4131-925a-29f58f89f84d)

![thumbnail_image](https://github.com/user-attachments/assets/edd60bde-64f1-4d16-acf3-25cabf0d6be8)


**These tools were essential in:**

  - Verifying that Cloudflare’s A record was correctly set.
  - Checking for DNS propagation delays.
  - Confirming that the EC2 instance was reachable via the domain name.

---

### Key Takeaways & Conclusion


| Takeaway                            | Description                                                                                  |
| ----------------------------------- | -------------------------------------------------------------------------------------------- |
| **DNS & A Records**                 | Gained hands-on experience configuring A records to map a domain to a server.                |
| **Web Server Deployment**           | Successfully hosted a public-facing NGINX server accessible via a custom domain.             |
| **Security Groups & Accessibility** | Understood and applied AWS security group rules to control traffic and ensure proper access. |
| **End-to-End Project Delivery**     | Carried out the full lifecycle — from domain registration to server setup and deployment.    |

---

This project was a valuable opportunity to bridge theory and practice in the field of networking and cloud computing. By deploying a **fully functional NGINX web server on an AWS EC2 instance and integrating it with a custom domain via Cloudflare,** I demonstrated understanding in real-world infrastructure setup, domain management, and web server configuration.

Beyond the technical implementation, customising the NGINX homepage by adding a personal touch allowed me to reflect on my understanding of user experience and presentation 

Overall, this project not only deepened my knowledge of core networking principles but also deepened my ability to deploy, troubleshoot, and maintain a publicly accessible web service from end to end.

---

### Acknowledgments

Thanks to:
AWS Documentation
NGINX Docs
Cloudflare Support Articles

