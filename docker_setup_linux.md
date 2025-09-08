# Docker Project Setup (Linux)

## Context
Docker is a platform for containerizing applications. It allows you to package applications with their dependencies into lightweight, portable containers that run consistently across environments. Containers are isolated, fast to start and stop, and ideal for modern development and deployment.

In this project, you will create an infrastructure that includes:
- A reverse proxy and load balancer
- Two API servers
- One front-end static content server

This setup will demonstrate routing, load balancing, and separation of services using Docker.

---

## High-Level Design
The architecture uses a single entry-point server acting as both a reverse proxy and a load balancer:

- **Front-end server**: Serves static content. All client requests go through the proxy, not directly to the front-end.
- **API servers**: Two servers handle API requests. The proxy distributes traffic between them using **Round Robin load balancing**.

**Round Robin Load Balancing**  
Requests are assigned to servers in a rotating order. For example:  
Request 1 → Server A, Request 2 → Server B, Request 3 → Server A, and so on.  
This evenly spreads requests across servers.

---

## Install Docker on Linux (Ubuntu/Debian Example)

### Step 1: Update system packages
```bash
sudo apt update
sudo apt upgrade -y
```

### Step 2: Install required dependencies
```bash
sudo apt install -y ca-certificates curl gnupg lsb-release
```

### Step 3: Add Docker’s official GPG key
```bash
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

### Step 4: Add Docker repository
```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Step 5: Install Docker Engine
```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### Step 6: Verify installation
```bash
docker --version
```

### Step 7 (Optional): Run Docker as non-root user
```bash
sudo usermod -aG docker $USER
newgrp docker
```

### Step 8: Test Docker
```bash
docker run hello-world
```
