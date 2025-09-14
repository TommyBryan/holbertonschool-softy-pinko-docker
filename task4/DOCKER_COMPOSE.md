# 🐳 Docker Compose Guide

## 🔹 What is Docker Compose?

**Docker Compose** is a tool that lets you **define and manage multi-container Docker applications**.  
Instead of starting containers one by one with long `docker run` commands, you can write all your services, networks, and volumes in a single **`docker-compose.yml` file**.  
Then, with a single command (`docker compose up`), Docker will start everything for you.

---

## 🔹 Why use it?

Imagine you’re building a web app:
- One container runs **Flask** (your backend).
- Another runs a **PostgreSQL** database.
- Another runs **Redis** for caching.

Without Docker Compose:
- You’d have to run multiple `docker run ...` commands manually.
- You’d need to configure networks and ports yourself.
- Harder to reproduce your environment.

With Docker Compose:
- You define everything in **one YAML file**.
- You start all services together with **one command**.
- Easy to share setup with your team.

---

## 🔹 Example: Flask + Redis App

Here’s a simple `docker-compose.yml` file:

```yaml
version: "3.9"

services:
  web:
    build: .
    ports:
      - "5000:5000"
    depends_on:
      - redis

  redis:
    image: "redis:alpine"

