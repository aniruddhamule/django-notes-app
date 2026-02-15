# 🚀 Django Notes App – Dockerized on AWS EC2

## 📌 Project Overview

This project is a production-style Django Notes Application deployed on AWS EC2 using Docker and Docker Compose.

The application follows a multi-container architecture:

- Nginx 
- Django (Application Server)
- MySQL (Database)
- Docker Network (Internal Communication)
- AWS EC2 (Infrastructure Host)

---

# 🏗 Architecture Diagram
<img width="2816" height="1536" alt="Gemini_Generated_Image_vtrywcvtrywcvtry" src="https://github.com/user-attachments/assets/20c8e093-2ab3-4564-9587-6d1eada39142" />

---

# ⚙️ How This Project Works (Step-by-Step)

## 1️⃣ User Request Flow

1. User hits EC2 Public IP in browser.
2. Request reaches EC2 instance.
3. Port 80 is exposed via Docker.
4. Nginx container receives request.
5. Nginx forwards request to Django container.
6. Django processes logic.
7. Django communicates with MySQL container.
8. Response flows back to user.

---

# ☁ AWS EC2 Setup

## 1️⃣ Connect to EC2

```bash
ssh -i your-key.pem ubuntu@<EC2_PUBLIC_IP>

2️⃣ Install Docker
sudo apt update -y
sudo apt install docker.io -y
docker --version
sudo systemctl start docker
sudo systemctl enable docker

3️⃣ Install Docker Compose
sudo apt install docker-compose -y
Verify:
docker compose version

📦 Clone Repository
git clone https://github.com/aniruddhamule/django-notes-app.git
cd django-notes-app

🐳 Build & Run Application
docker compose up --build -d

What This Command Does:

Builds Django image
Builds Nginx image
Pulls MySQL image
Creates Docker network
Creates volumes
Starts all containers

🔍 Verify Containers
docker ps

Expected containers:
nginx_cont
django_cont
db_cont

📊 Check Container Logs
Nginx Logs
docker logs nginx_cont

Django Logs
docker logs django_cont

MySQL Logs
docker logs db_cont

🌐 Access Application

Open in browser:

http://<EC2_PUBLIC_IP>
🐳 Docker Networking Explanation

Docker Compose automatically creates a bridge network.

Containers communicate using service names defined in docker-compose.yml.

Example:

Django connects to MySQL using:

DB_HOST=db_cont


Nginx forwards traffic to:

django_cont:8000


MySQL is NOT publicly exposed.

🗄 Database Persistence

MySQL uses a Docker volume:

mysql-data/


This ensures database data is not lost when containers restart.

🔁 Restart / Rebuild Application

If code changes:

docker compose down
docker compose up --build -d

🛑 Stop Application
docker compose down

📁 Project Structure
<img width="1124" height="436" alt="Screenshot 2026-02-15 001738" src="https://github.com/user-attachments/assets/d4a0ba0c-6cf9-4c9a-bcac-af1d80240edd" />


# 📸 Screenshots

## 📝 Notes Application UI
<img width="1360" height="768" alt="Screenshot 2026-02-15 001106" src="https://github.com/user-attachments/assets/0ce11cc7-874b-4c66-be0d-ce7fbb64d67c" />

---
## ☁ AWS EC2 Instance Running

<img width="1360" height="655" alt="Screenshot 2026-02-15 001245" src="https://github.com/user-attachments/assets/71877369-4649-43c7-b9fb-6c85ae3ea176" />

---

## 🐳 Docker Build & Containers

<img width="1110" height="485" alt="Screenshot 2026-02-15 001426" src="https://github.com/user-attachments/assets/1b599d99-51f6-4355-8c84-8d545beb2b3b" />

---

## 🔍 Nginx Logs (Live Traffic)

<img width="1132" height="364" alt="Screenshot 2026-02-15 001535" src="https://github.com/user-attachments/assets/ee2a62f7-5070-44b4-9b18-aed9eeecbb20" />

---

## 📂 Project Structure















