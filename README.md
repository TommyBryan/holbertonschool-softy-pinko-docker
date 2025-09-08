# holbertonschool-softy-pinko-docker

# Docker Project Setup

## Context
Docker is a platform for containerizing applications. It allows you to package applications with their dependencies into lightweight, portable containers that run consistently across different environments. Containers are isolated, fast to start and stop, and ideal for modern development and deployment.

In this project, you will create an infrastructure that includes:
- A reverse proxy and load balancer
- Two API servers
- One front-end static content server

This setup will demonstrate how to handle routing, load balancing, and separation of services using Docker.

---

## High-Level Design
The architecture uses a single entry-point server acting as both a reverse proxy and a load balancer:

- **Front-end server**: Serves static content. All client requests go through the proxy, not directly to the front-end.
- **API servers**: Two servers handle API requests. The proxy distributes traffic between them using **Round Robin load balancing**.

**Round Robin Load Balancing**  
Requests are assigned to servers in order, one after another, cycling back to the first server. For example:  
Request 1 → Server A, Request 2 → Server B, Request 3 → Server A, and so on.  
This evenly spreads requests across servers.

---

## Requirements Before Starting
1. **Install Docker Desktop**  
   Download and install Docker Desktop from:  
   [https://www.docker.com/](https://www.docker.com/)

   Installation guides:
   - [Windows](https://docs.docker.com/desktop/install/windows/)
   - [Mac](https://docs.docker.com/desktop/install/mac/)
   - [Linux](https://docs.docker.com/engine/install/)

   Note: On Chromebooks, you may install Docker Engine, but Docker Desktop is not supported. It is recommended to use Windows, Mac, or Linux instead.

2. **Learn Docker basics**  
   - [Docker Tutorial](https://docs.docker.com/get-started/)

---

## Next Steps
- Set up Docker containers for the proxy, API servers, and front-end.
- Configure the reverse proxy and load balancing logic.
- Test the system by sending requests and observing how they are routed.
