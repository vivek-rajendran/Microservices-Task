# Microservices-Task

## Overview

This project demonstrates containerization and orchestration of Node.js microservices using Docker and Docker Compose.

The application consists of:

* User Service (Port 3000)
* Product Service (Port 3001)
* Gateway Service (Port 3003)

All services are containerized using Docker and connected through a shared Docker bridge network using Docker Compose.

---

## Prerequisites

* Docker Installed
* Docker Compose Installed

Verify installation:

```bash
docker --version
docker compose version
```

---

## Project Structure

```text
Microservices-Task/
├── user-service/
│   ├── Dockerfile
│   ├── app.js
│   └── package.json
├── product-service/
│   ├── Dockerfile
│   ├── app.js
│   └── package.json
├── gateway-service/
│   ├── Dockerfile
│   ├── app.js
│   └── package.json
├── docker-compose.yml
└── README.md
```

---

## Build Application

Build all Docker images:

```bash
docker compose build
```

For a clean rebuild:

```bash
docker compose build --no-cache
```

---

## Start Application

Run all services:

```bash
docker compose up
```

Or run in detached mode:

```bash
docker compose up -d
```

---

## Verify Running Containers

```bash
docker ps
```

Expected containers:

```text
user-service
product-service
gateway-service
```

---

## Services and Endpoints

### User Service

* Base URL: `http://localhost:3000`

**List Users**

```bash
curl http://localhost:3000/users
```

Or open in browser:

```text
http://localhost:3000/users
```

---

### Product Service

* Base URL: `http://localhost:3001`

**List Products**

```bash
curl http://localhost:3001/products
```

Or open in browser:

```text
http://localhost:3001/products
```

---

### Gateway Service

* Base URL: `http://localhost:3003/api`

**Users**

```bash
curl http://localhost:3003/api/users
```

**Products**

```bash
curl http://localhost:3003/api/products
```

---

## Docker Network

All services communicate through a shared Docker bridge network:

```text
microservices-network
```

Service communication:

```text
Gateway Service
     |
     +----> User Service
     |
     +----> Product Service
```

---

## View Logs

View logs for all services:

```bash
docker compose logs
```

View logs for a specific service:

```bash
docker compose logs gateway-service
```

---

## Stop Application

```bash
docker compose down
```

---

## Troubleshooting

### Containers Not Starting

Check logs:

```bash
docker compose logs
```

### Verify Container Status

```bash
docker ps -a
```

### Rebuild Containers

```bash
docker compose down
docker compose build --no-cache
docker compose up
```

### Port Already in Use

Windows:

```bash
netstat -ano | findstr :3000
```

Terminate the conflicting process or modify the port mapping.

---

## Testing & Validation

1. Build all Docker images.
2. Start all services using Docker Compose.
3. Verify containers using `docker ps`.
4. Test all service endpoints.
5. Confirm successful responses from User, Product, and Gateway services.

---

## Screenshots

Include screenshots showing:

1. Successful Docker image build (`docker compose build`)
2. Successful application startup (`docker compose up`)
3. Running containers (`docker ps`)
4. User Service endpoint response
5. Product Service endpoint response
6. Gateway Service endpoint response

---

## Learning Outcome

Through this assignment, I gained hands-on experience with:

* Docker image creation using Dockerfiles
* Node.js application containerization
* Docker Compose orchestration
* Docker networking and service communication
* Container lifecycle management and troubleshooting