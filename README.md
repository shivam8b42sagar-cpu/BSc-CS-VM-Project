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
echo "<h1>Hello World from Apache on AWS EC2!</h1>" | sudo tee /var/www/html/index.html
sudo systemctl restart apache2
sudo apt update -y
sudo apt install ca-certificates curl gnupg -y
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update -y
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
sudo systemctl enable docker
sudo systemctl start docker
sudo usermod -aG docker $USER
docker run hello-world
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
minikube start --driver=docker
kubectl get nodes
curl -sfL https://get.k3s.io | sh -
sudo systemctl status k3s
sudo k3s kubectl get nodes



