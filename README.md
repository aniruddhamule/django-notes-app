🚀 Django Notes App – Dockerized Deployment on AWS EC2
📌 Project Overview

This is a full-stack Django Notes Application containerized using Docker and deployed on an AWS EC2 instance.

The project demonstrates:

Docker containerization

Multi-container architecture using Docker Compose

Nginx reverse proxy

MySQL database container

Deployment on AWS EC2

Production-style setup

🏗 High-Level Architecture

Architecture Flow
Users
   ↓
EC2 Instance (Docker Host)
   ↓
Docker Network
   ├── Nginx Container (Reverse Proxy)
   ├── Django Container (App Server)
   └── MySQL Container (Database)

🧱 Tech Stack

Python 3.9

Django

MySQL

Nginx

Docker

Docker Compose

AWS EC2 (t2.medium)

🖥 Live Deployment

The application is deployed on:

http://54.193.131.221

📸 Application Screenshots
📝 Notes UI

☁ AWS EC2 Instance

🐳 Docker Build & Containers Running

🔍 Nginx Logs (Live Traffic)

📂 Project Structure

🐳 Docker Architecture Details
1️⃣ Nginx Container

Acts as reverse proxy

Handles static files

Forwards requests to Django container

2️⃣ Django Container

Runs the application

Connects to MySQL via Docker network

Uses environment variables from .env

3️⃣ MySQL Container

Stores notes and user data

Persistent volume mounted

📦 Docker Compose Setup

To run locally:

git clone https://github.com/aniruddhamule/django-notes-app.git
cd django-notes-app

docker compose up --build


Stop containers:

docker compose down

⚙️ Environment Variables

Create .env file:

DB_NAME=notes_db
DB_USER=root
DB_PASSWORD=yourpassword
DB_HOST=db_cont
DB_PORT=3306

🌐 Nginx Reverse Proxy

Nginx configuration forwards traffic to Django:

location / {
    proxy_pass http://django_cont:8000;
}

🗂 Folder Structure
django-notes-app/
│
├── api/
├── mynotes/
├── notesapp/
├── nginx/
├── mysql-data/
├── Dockerfile
├── docker-compose.yml
├── manage.py
└── requirements.txt

🚀 Deployment Steps (AWS EC2)

Launch EC2 (Ubuntu)

Install Docker & Docker Compose

Clone repository

Run:

docker compose up --build -d


Open EC2 Public IP in browser

📊 Production Highlights

✔ Multi-container setup
✔ Reverse proxy architecture
✔ Persistent MySQL storage
✔ Cloud deployment
✔ Real traffic logs verified
✔ Clean container networking

🛡 Security Notes

Runs behind Nginx

Port exposure handled via Docker

MySQL not publicly exposed

Can be upgraded with SSL (Let’s Encrypt)

📈 Future Improvements

Add HTTPS with Certbot

Use AWS RDS instead of container MySQL

Add CI/CD with GitHub Actions

Implement Load Balancer

Add Redis caching
