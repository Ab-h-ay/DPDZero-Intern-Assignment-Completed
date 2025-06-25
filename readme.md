# 🚀 DPDZero Intern Assignment – Full Dockerized Microservices with Nginx Reverse Proxy

This project is part of the DPDZero DevOps Internship assignment. It demonstrates how to containerize and orchestrate two backend services (written in Go and Python) using Docker and Docker Compose, and route requests via an Nginx reverse proxy.

---
---

## ☁️ AWS Infrastructure Setup

The project was deployed and tested on an **Ubuntu-based AWS EC2 instance** using the following steps:

### ✅ 1. Launch EC2 Instance

- Go to [AWS EC2 Dashboard](https://console.aws.amazon.com/ec2/)
- Click **"Launch Instance"**
- **AMI**: Ubuntu Server 22.04 LTS (or latest stable)
- **Instance type**: t2.micro (Free Tier eligible)
- **Key pair**: Create new or use existing to SSH
- **Security Group**:
  - Allow inbound traffic on:
    - **22** (SSH)
    - **8080** (App access via Nginx)
    -  allow **80** and **443** for web apps)
    -  **8001-8002** (for ping and hello)

### ✅ 2. SSH into EC2 Instance
ssh -i your-key.pem ubuntu@<EC2_PUBLIC_IP>

## 📦 Tech Stack

- **Golang (Service 1)** – Simple HTTP server with `/ping` and `/hello` endpoints
- **Python + Flask (Service 2)** – REST API with `/ping` and `/hello`
- **Nginx** – Reverse proxy to route requests to the two services
- **Docker & Docker Compose** – Containerization and orchestration
- **Bridge Networking** – All services are connected through Docker’s internal bridge network

---

## 📁 Project Structure
DPDZero-Intern-Assignment/
├── docker-compose.yml
├── nginx/
│ ├── Dockerfile
│ └── nginx.conf
├── service_1/
│ ├── Dockerfile
│ └── main.go
├── service_2/
│ ├── Dockerfile
│ ├── app.py
│ └── requirements.txt
└── README.md

---

## ⚙️ Technologies Used

- Docker
- Docker Compose
- Nginx
- Python 3.10 + Flask
- Golang 1.22 (Alpine)
- Alpine Linux for lightweight images

---

## 🔧 Setup Instructions

> 💡 Prerequisites:
> - Docker & Docker Compose installed
> - Port `8080` open on your system or EC2 instance

### ✅ To Build and Run Everything:

git clone https://github.com/<your-username>/DPDZero-Intern-Assignment.git
cd DPDZero-Intern-Assignment
docker-compose up --build

🌐 API Endpoints
Path	Service	Description
/service1/ping	Golang	Health check
/service1/hello	Golang	Returns Hello message
/service2/ping	Flask	Health check
/service2/hello	Flask	Returns Hello message

Example (on local or EC2):
http://localhost:8080/service1/hello
http://localhost:8080/service2/hello

If hosted on EC2:
http://<your-ec2-public-ip>:8080/service2/ping

🧪 Testing
After running the containers, test with:
curl http://localhost:8080/service1/ping
curl http://localhost:8080/service2/hello

🧼 Cleanup
Stop and remove containers, networks, and images:
docker-compose down --volumes --remove-orphans
