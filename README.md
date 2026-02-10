# Strapi Docker Setup with PostgreSQL and Nginx

## Overview
This project demonstrates how to run a Strapi application using Docker Compose with:
- PostgreSQL as the database
- Nginx as a reverse proxy
- A user-defined Docker network for inter-container communication

The setup allows accessing the Strapi Admin Dashboard via Nginx on port 80.

---

## Architecture
- **Strapi** runs on internal port `1337`
- **PostgreSQL** is used as the database
- **Nginx** acts as a reverse proxy
- All services run on a custom Docker network: `strapi-net`

---

## Services

### 1. PostgreSQL
- Image: `postgres:15`
- Environment variables:
  - `POSTGRES_DB=strapi`
  - `POSTGRES_USER=strapi`
  - `POSTGRES_PASSWORD=strapi`
- Uses a named volume for data persistence

### 2. Strapi
- Built using a custom Dockerfile
- Connects to PostgreSQL using environment variables
- Runs on internal port `1337`

### 3. Nginx
- Image: `nginx:alpine`
- Exposes port `80` on the host
- Proxies requests from `http://localhost` to `http://strapi:1337`

---

## Docker Network
A user-defined Docker network named `strapi-net` is created and shared by:
- PostgreSQL
- Strapi
- Nginx

This enables container-to-container communication using service names.

---

## How to Run the Project

### Prerequisites
- Docker
- Docker Compose

### Steps
```bash
docker compose build
docker compose up
