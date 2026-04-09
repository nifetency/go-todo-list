# Go Todo

![hero](https://res.cloudinary.com/ichtrojan/image/upload/v1574958373/Screenshot_2019-11-28_at_17.22.25_gyegdr.png)

## Introduction

A simple todolist application written in Go 

## Requirements
* MySQL installed
* Go installed

## Installation

* Clone this repo 

```bash
git clone https://github.com/ichtrojan/go-todo.git
```

* Change Directory

```bash
cd go-todo
```

* Initiate `.env` file

```bash
cp .env.example .env
```

* Modify `.env` file with your correct database credentials and desired Port

## Usage

To run this application, execute:

```bash
go run main.go
```

You should be able to access this application at `http://127.0.0.1:4040`

>**NOTE**<br>
>If you modified the port in the `.env` file, you should access the application for the port you set

## Conclusion 

This Project is an example to teach CRUD using the default `database/sql` package and how to serve html templates properly.

If you have anything to add to this, please send in a PR as it will no longer be actively maintained by [me](https://github.com/ichtrojan).

## Deployment on NIFE

Deploy your application using the NIFE platform:

https://launch.nife.io/

Deployment flow:

```
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

* Source: Docker Image
* Registry: Docker Hub
* Image: `<username>/go-todo-list:latest`
* Tag: `latest`

---

### Step 3: Build Configuration

* Internal Port: `4040`
* External Port: `80`

Environment variables:

| Key     | Value              |
| ------- | ------------------ |
| DB_HOST | your-database-host |
| DB_USER | your-username      |
| DB_PASS | your-password      |
| DB_NAME | your-database-name |
| PORT    | 4040               |

---

### Step 4: Resources Configuration

* Region: e.g., `ap-south-1`
* Resource Type: CPU

Recommended settings:

* CPU Request: `250m`
* Memory Request: `512MB`
* CPU Limit: `500m`
* Memory Limit: `1GB`

---

### Step 5: Deploy

* Strategy: Rolling
* Workload: Deployment
* Routing Policy: Latency
* Replicas: 1–2

Click Deploy.

---

## Method 2: Deploy via Git Repository

### Step 1: Select Source

* Source: Git Repository
* Provider: GitHub
* Branch: `main`

---

### Step 2: Build Configuration

* Internal Port: `4040`
* External Port: `80`

Enable:

```
Auto-Dockerize with Runtime
```

---

### Step 3: Build and Security

NIFE automatically performs:

* SAST
* SCA
* Container scan
* IaC scan

Resolve any critical issues before proceeding.

---

### Step 4: Resources and Deploy

Use the recommended configuration above and deploy.

---

## Deployment using nifectl (CLI)

You can deploy the application using the nifectl CLI.

---

### Install nifectl CLI (Windows)

#### 1. Download

https://github.com/nifetency/nifectl/releases/tag/v4.1.3-dev

Download:

```
nifectl-windows-amd64.zip
```

---

#### 2. Extract

* Right-click the ZIP file
* Select Extract All
* Open the extracted folder

---

#### 3. Open Terminal

* Type `cmd` in the address bar
  or
* Right-click and select Open in Terminal

---

#### 4. Verify Installation

```bash
nifectl --help
```

---

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

* Application name
* Organization
* Repository URL
* Branch (`main`)

---

### Step 3: Configure Deployment

* Deployment Type: Deployment
* Resource Type: CPU
* Replicas: 1

Ports:

* Internal: `4040`
* External: `80`

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

* Validation
* Build
* Deployment

---

### Step 7: Access Application

```
https://<your-nife-url>
```

---


## Dependencies

| Dependency     | Purpose              |
| -------------- | -------------------- |
| Go             | Runtime environment  |
| MySQL          | Database             |
| database/sql   | Database interaction |
| HTML Templates | UI rendering         |

---

## Environment Variables

| Variable | Description       | Example   |
| -------- | ----------------- | --------- |
| DB_HOST  | Database host     | localhost |
| DB_USER  | Database username | root      |
| DB_PASS  | Database password | password  |
| DB_NAME  | Database name     | todo_db   |
| PORT     | Application port  | 4040      |

---

## Troubleshooting

| Issue                    | Solution                                          |
| ------------------------ | ------------------------------------------------- |
| Port already in use      | Change PORT in `.env` or stop the running process |
| MySQL connection failed  | Verify DB credentials and ensure MySQL is running |
| App not starting         | Check `.env` configuration and logs               |
| Go not installed         | Install Go and verify with `go version`           |
| Dependencies missing     | Run `go mod tidy`                                 |
| Docker build fails       | Ensure Dockerfile is correct                      |
| Deployment fails on NIFE | Verify ports, env variables, and logs             |
| App not accessible       | Check routing and port configuration              |
| Database not reachable   | Ensure DB is accessible from deployment           |

---
