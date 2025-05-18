# 🚀 MERN Stack Dockerized with Docker Compose

![Docker](https://img.shields.io/badge/Docker-blue?logo=docker)
![Docker Compose](https://img.shields.io/badge/Docker%20Engine-blue?logo=docker)
![MongoDB](https://img.shields.io/badge/MongoDB-brightgreen?logo=mongodb)
![Express](https://img.shields.io/badge/Express.js-lightgrey?logo=express)
![React](https://img.shields.io/badge/React-blue?logo=react)
![Node.js](https://img.shields.io/badge/Node.js-green?logo=node.js)
![License](https://img.shields.io/badge/license-MIT-blue)
![Status](https://img.shields.io/badge/status-Active-brightgreen)

This project demonstrates containerizing a MERN stack (MongoDB, Express, React, Node.js) by building separate Docker images for frontend and backend services, running MongoDB as a container, setting up a custom Docker network, and orchestrating all services with Docker Compose.

---

## 🛠️ Technologies Used

- **Docker** & **Docker Compose**
- **MongoDB**
- **Express**
- **Node.js**
- **React**

---

## ⚙️ Setup and Usage

> For testing purposes, each container (frontend, backend, and MongoDB) was tested manually before integrating with Docker Compose.

### 1️⃣ Build Frontend Docker Image

```bash
cd mern/frontend
docker build -t mern-frontend .
docker run -d -p 5173:5173 --name frontend mern-frontend
```

![image](https://github.com/user-attachments/assets/ca3bdc43-664e-4bd3-8fe1-c18f7b8759c8)
![docker run container](https://github.com/user-attachments/assets/c642fd02-45fc-40a0-80ef-32a86b261a1f)

### 2️⃣ Run MongoDB Container with Persistent Data Using Host Bind Mount

A local directory on the host machine is mounted to persist MongoDB data.

```bash
docker run --network=mern --name mongodb -d -p 27017:27017 -v ~/opt/data:/data/db mongo:latest
```

![Pullling the mongo](https://github.com/user-attachments/assets/5dbf53f9-fb7c-4734-bb20-92fc1e10ccd1)

### 3️⃣ Build & Run Backend Docker Image

```bash
cd mern/backend
docker build -t mern-backend .
docker run --name=backend --network=mern -d -p 5050:5050 mern-backend
```

![build backend](https://github.com/user-attachments/assets/2de78cc7-87d7-48dc-886f-f796756b9ff7)
![backend run docker](https://github.com/user-attachments/assets/397a2c6a-bbd2-4d6a-8f8d-a001ee5148c7)

### 4️⃣ Create Custom Docker Network

Attach running containers to this network to enable seamless inter-service communication.

```bash
docker network create mern
```

![network create](https://github.com/user-attachments/assets/38665632-42aa-49af-8b45-caebaac9e36c)
![Networks ls](https://github.com/user-attachments/assets/f3144de2-5d98-490a-a14d-87fb4db3b597)

### 5️⃣ Orchestrate Services with Docker Compose

The docker-compose.yml manages service definitions, network configuration, volumes, and startup order.
Start all services:

```bash
docker compose up -d
```

![Docker compose up](https://github.com/user-attachments/assets/9f83b210-4444-47ca-9341-3dc008269818)
![compose up](https://github.com/user-attachments/assets/ddfbbd38-895b-4087-a78a-124d4451a9f2)

Stop all services:

```bash
docker compose down
```

This is a test edit  to trigger the Jenkins freestyle project.
