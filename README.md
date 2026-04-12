# Go Todo Application

## Overview

A simple to-do list application written in Go.

This project demonstrates:
- CRUD operations using Go
- Database interaction using `database/sql`
- Serving HTML templates

It is useful for:
- Learning Go backend development
- Understanding database integration
- Practicing full-stack basics

---

## Requirements

Make sure you have the following installed:

- Go
- MySQL
- Git

---

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/ichtrojan/go-todo.git
cd go-todo
```

---

### 2. Setup Environment File

```bash
cp .env.example .env
```

Update `.env` with your database credentials and desired port.

---

### 3. Run the Application

```bash
go run main.go
```

---

### 4. Open in Browser

Visit:

```
http://127.0.0.1:4040
```

Note: If you changed the port in `.env`, use that port instead.

---

## Features

- Create, Read, Update, Delete (CRUD) operations
- MySQL database integration
- Server-side HTML rendering

---

## Deployment on NIFE

Deploy your application using the NIFE platform:

https://launch.nife.io/

Deployment flow:

```text
Source → Build → Resources → Review → Deploy
```

Prerequisite: Ensure a workload (Deployment, CronJob, or StatefulSet) exists.

---

## Method 1: Deploy via Docker Image (Recommended)

### Step 1: Build and Push Image

```bash
docker build -t go-todo-list .
docker tag go-todo-list <username>/go-todo-list:latest
docker push <username>/go-todo-list:latest
```

---

### Step 2: Configure Source

- Source: Docker Image
- Registry: Docker Hub
- Image: `<username>/go-todo-list:latest`
- Tag: `latest`

---

### Step 3: Build Configuration

- Internal Port: `4040`
- External Port: `80`

Environment variables:

| Key     | Value              |
|---------|--------------------|
| DB_HOST | your-database-host |
| DB_USER | your-username      |
| DB_PASS | your-password      |
| DB_NAME | your-database-name |
| PORT    | 4040               |

---

### Step 4: Resources Configuration

- Region: e.g., `ap-south-1`
- Resource Type: CPU

Recommended settings:

- CPU Request: `250m`
- Memory Request: `512MB`
- CPU Limit: `500m`
- Memory Limit: `1GB`

---

### Step 5: Deploy

- Strategy: Rolling
- Workload: Deployment
- Routing Policy: Latency
- Replicas: 1–2

Click **Deploy**.

---

## Method 2: Deploy via Git Repository

### Step 1: Select Source

- Source: Git Repository
- Provider: GitHub
- Branch: `main`

---

### Step 2: Build Configuration

- Internal Port: `4040`
- External Port: `80`

Enable:

```
Auto-Dockerize with Runtime
```

---

### Step 3: Build and Security

NIFE automatically performs:

- SAST
- SCA
- Container scan
- IaC scan

Resolve any critical issues before proceeding.

---

### Step 4: Resources and Deploy

Use the recommended configuration above and deploy.

---

## Deployment using nifectl (CLI)

### Step 1: Download nifectl

https://docs.nife.io/Quick-Start/Nifectl

---

### Step 2: Open Terminal

- Type `cmd` in the address bar  
  OR  
- Right-click → **Open in Terminal**

---

### Step 3: Verify Installation

```bash
nifectl --help
```

---

## Deployment Steps

### Step 1: Login

```bash
nifectl auth login
```

---

### Step 2: Initialize Project

```bash
nifectl init
```

Provide:
- Application name
- Organization
- Repository URL
- Branch (`main`)

---

### Step 3: Configure Deployment

- Deployment Type: Deployment
- Resource Type: CPU
- Replicas: 1

Ports:
- Internal: `4040`
- External: `80`

---

### Step 4: Deploy

```bash
nifectl deploy
```

---

### Step 5: Select Region

Example:

```
IND - Mumbai
```

---

### Step 6: Monitor Deployment

Monitor logs for:
- Validation
- Build
- Deployment

---

### Step 7: Access Application

```
https://<your-nife-url>
```

---

## Dependencies

| Dependency     | Purpose              |
|----------------|----------------------|
| Go             | Runtime environment  |
| MySQL          | Database             |
| database/sql   | Database interaction |
| HTML Templates | UI rendering         |

---

## Environment Variables

| Variable | Description       | Example   |
|----------|------------------|-----------|
| DB_HOST  | Database host     | localhost |
| DB_USER  | Database username | root      |
| DB_PASS  | Database password | password  |
| DB_NAME  | Database name     | todo_db   |
| PORT     | Application port  | 4040      |

---

## Troubleshooting

| Issue                   | Solution                                          |
|------------------------|--------------------------------------------------|
| Port already in use    | Change PORT or stop running process              |
| MySQL connection failed| Verify DB credentials and MySQL service          |
| App not starting       | Check `.env` configuration and logs              |
| Go not installed       | Install Go and verify with `go version`          |
| Dependencies missing   | Run `go mod tidy`                                |
| Docker build fails     | Verify Dockerfile                                |
| Deployment fails       | Check logs, ports, and environment variables     |
| App not accessible     | Verify routing and port mapping                  |
| DB not reachable       | Ensure database is accessible                    |

---

## Acknowledgements

This repository is maintained by Nifetency as a sample deployment project for Nife.io.

If derived from an upstream example, proper credit should be given to the original author.

---

## License

This project is licensed under the MIT License.

---

## References

- Original Repository: https://github.com/ichtrojan/go-todo
- NIFE Platform: https://nife.io/