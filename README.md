# Expense Tracker Deployment on AWS EC2 using Docker Compose

## Overview

This project demonstrates the deployment of a containerized Expense Tracker application on AWS EC2 using Docker and Docker Compose.

The application consists of a Spring Boot backend, MySQL database, and Nginx web server running as separate containers connected through a Docker network.

The original application source code is based on an open-source project. My contribution focused on infrastructure provisioning, container deployment, networking, and cloud hosting using AWS.

---

## Architecture

```text
Internet
    |
 AWS EC2 (Ubuntu)
    |
 Docker Compose
 ├── Nginx Container
 ├── Spring Boot Container
 └── MySQL Container
```

---

## Technologies Used

* AWS EC2
* Ubuntu Linux
* Docker
* Docker Compose
* Spring Boot
* MySQL
* Nginx
* Git & GitHub

---

## Docker Services

### Spring Boot Application

* Java 17
* Spring Boot Framework
* Runs on port 8080
* Connects to MySQL container through Docker network

### MySQL Database

* MySQL latest image
* Persistent storage using Docker volumes
* Stores user and expense data

### Nginx

* Acts as a web server/reverse proxy
* Routes incoming traffic to the application container

---

## Infrastructure Details

| Component         | Value    |
| ----------------- | -------- |
| Cloud Provider    | AWS      |
| Service           | EC2      |
| OS                | Ubuntu   |
| Instance Type     | t3.small |
| Application Port  | 8080     |
| Database          | MySQL    |
| Container Runtime | Docker   |

---

## Deployment Steps

### 1. Launch EC2 Instance

Create an Ubuntu EC2 instance and configure the security group to allow:

* SSH (22)
* HTTP (80)
* Application Port (8080)

### 2. Install Docker

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl enable docker
sudo systemctl start docker
```

### 3. Install Docker Compose

```bash
docker compose version
```

### 4. Clone Repository

```bash
git clone <repository-url>
cd Expenses-Tracker-WebApp
```

### 5. Start Containers

```bash
docker compose up -d
```

### 6. Verify Running Containers

```bash
docker ps
```

### 7. Access Application

```text
http://13.50.241.198:8080/
```

---

## Screenshots

### Application Homepage

application page (<img width="1600" height="900" alt="website" src="https://github.com/user-attachments/assets/e0706e52-5019-4368-a3ff-f1b8c00e47f0" />)


### Login Page

![Login] (<img width="1600" height="900" alt="website 2" src="https://github.com/user-attachments/assets/14f76189-4748-4600-bf1d-5b61f99f1481" />
)

### AWS EC2 Instance

![EC2] (<img width="1600" height="900" alt="ec2 instance" src="https://github.com/user-attachments/assets/17d67802-67f0-451a-a613-852c657e9491" />
)

### Security Group Configuration

![Security Group] (<img width="1600" height="900" alt="security 8080 port" src="https://github.com/user-attachments/assets/9db4d7ad-2c7e-4f4c-a8a7-8d7c3e0f1ec0" />
)

### Running Containers

![Docker] (<img width="1600" height="900" alt="docker containers" src="https://github.com/user-attachments/assets/dd275506-0f55-4fa2-8925-42e9867786d3" />
)

---

## Docker Network Design

All containers communicate through a custom Docker network:

```yaml
networks:
  appbridge:
```

This allows the Spring Boot application to connect to MySQL using the service name:

```text
mysql:3306
```

instead of a public IP address.

---

## Skills Demonstrated

* Linux Administration
* Docker Containerization
* Docker Compose
* Multi-Container Applications
* AWS EC2 Deployment
* Container Networking
* MySQL Configuration
* Application Troubleshooting
* Infrastructure Documentation

---

## Challenges Faced

* Configuring AWS Security Groups
* Exposing Application Port 8080
* Container-to-Container Communication
* MySQL Connectivity
* Docker Network Configuration
* Application Startup Troubleshooting

---

## Future Improvements

* Configure Nginx Reverse Proxy
* Add Custom Domain
* Enable HTTPS using Let's Encrypt
* Implement GitHub Actions CI/CD Pipeline
* Store Secrets using AWS Secrets Manager
* Deploy with Terraform
* Migrate to Kubernetes

---

## Author

Krishi Bokde

DevOps Learning Project focused on Docker, AWS, Linux, and Cloud Deployment.
