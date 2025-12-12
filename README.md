# Cloud Deployment Project

## Tools Used

| Tool                | Description |
|--------------------|-------------|
| AWS EC2            | Virtual machines in the AWS cloud used to host services. |
| Apache HTTP Server | Popular open-source web server for hosting websites. |
| Docker             | Platform to build, run, and manage containers. |
| Minikube           | Tool for running a single-node Kubernetes cluster locally. |
| K3s                | Lightweight Kubernetes distribution optimized for IoT and edge devices. |

---

## 🖼️ Project Diagrams / Images

<img src="cloud2.jpg" width="500">

---

## 1️⃣ Launch EC2 Instances

- **AMI:** Ubuntu 22.04 LTS  
- **Instance Type:** `t2.micro` (free tier)  
- **Security Group:** Allow inbound on ports **22 (SSH)**, **80 (HTTP)**, **443 (HTTPS)**

---

## 2️⃣ Install Apache Web Server

```bash
sudo apt update -y
sudo apt install apache2 -y
sudo systemctl enable apache2
sudo systemctl start apache2
curl http://localhost
3️⃣ Hello World Website
echo "<h1>Hello World from Apache on AWS EC2!</h1>" | sudo tee /var/www/html/index.html
sudo systemctl restart apache2
