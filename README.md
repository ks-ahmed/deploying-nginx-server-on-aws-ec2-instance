# Nginx on AWS EC2 with DNS routing using Cloudflare.


This project demonstrates designing and deploying of a real-world networked web-app by deploying an NGINX web server on an Amazon Web Service (AWS) EC2 instance and making it accessible via a custom domain using Cloudflare DNS.

---

## Overview

- Designing and deploying cloud-based network infrastructure.
- Understanding the core components of web traffic, server configuration, and DNS.
- Registering and configuring a custom domain with proper DNS records.

---

## Network Overview

- **IP Addressing & Subnetting** – Decoding public/private IPs and routing rules.
- **DNS** – Domain Name System fundamentals and record management.
- **Routing & Firewalls** – Configuring AWS security groups and routing inbound traffic.
- **Web Server Deployment** – Using NGINX to host and serve web content.
- **Cloud Infrastructure** – Launching and managing EC2 instances on AWS.
- **Domain Management** – Buying and configuring a domain via Cloudflare.
- **Network Security** – Restricting access and securing traffic flow.

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
Created an A record in Cloudflare DNS:
Host: nginx.vettlyai.com
Value: Public IP of EC2 instance
Waited for DNS propagation (~5–10 minutes).


---

### 5. 5. Custom Homepage 

To go beyond the basics and demonstrate creative thinking, I customized the default NGINX homepage:

Edited `/var/www/html/index.html` to showcase:
A clean, branded look matching `nginx.vettlyai.com.`
A welcome message explaining the purpose of the project.
Simple styling for clarity and professionalism.
using `sudo /var/www/html/index.html`

---

### BEFORE: Verified public accessibility through the NGINX landing page via the domain.

![Screenshot from 2025-05-19 16-13-10](https://github.com/user-attachments/assets/cb8282c9-3cae-4314-a57d-0bababa1962c)

---

### AFTER: Mapped custom domain `nginx.vettlyai.com` to the EC2 instance. 

![Screenshot from 2025-05-19 18-34-49](https://github.com/user-attachments/assets/e552d8d7-38f8-4b56-9a9b-4db5a003ceb5)


---

### ⚙️ Tools & Technologies

Amazon Web Services (EC2)
NGINX Web Server
Cloudflare DNS
Ubuntu Linux
Bash / Terminal
SSH

---

### Key Takeaways
Practical understanding of DNS and A records.
Real-world deployment of a public-facing web server.
Vital concepts of security group rules and network accessibility.
End-to-end experience from domain registration to live hosting.

---
### Screenshots (dig / nslookup)


![Screenshot from 2025-05-19 13-39-09](https://github.com/user-attachments/assets/458e80aa-4540-4131-925a-29f58f89f84d)

![Screenshot from 2025-05-18 19-59-13](https://github.com/user-attachments/assets/6e35ff24-a75e-42ab-a748-0d8579492ffd)


---

### Conclusion
This project was a valuable opportunity to bridge theory and practice in the field of networking and cloud computing. By deploying a **fully functional NGINX web server on an AWS EC2 instance and integrating it with a custom domain via Cloudflare,** I demonstrated understanding in real-world infrastructure setup, domain management, and web server configuration.

Beyond the technical implementation, customising the NGINX homepage by adding a personal touch allowed me to reflect on my understanding of user experience and presentation 

Overall, this project not only deepened my knowledge of core networking principles but also deepened my ability to deploy, troubleshoot, and maintain a publicly accessible web service from end to end.

---

### Acknowledgments

Thanks to:
AWS Documentation
NGINX Docs
Cloudflare Support Articles

