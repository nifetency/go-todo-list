# Go Todo Application

A simple **Go-based web application** published as a **sample deployment project for [Nife.io][1]**.

This repository demonstrates how to run a lightweight Go application locally, package it with Docker, and deploy it on [Nife.io][1]. It is intended as a practical sample for validating Go deployment workflows, container-based delivery, and basic platform configuration.[1][2]

---

## Overview

This project is a basic to-do list application built using Go with database integration. It demonstrates CRUD operations, server-side rendering, and backend development fundamentals.[3]

If you want a simple backend project to test deployment on [Nife.io][1], this repository is a good starting point.

---

## Features

| Feature                | Description                            |
| ---------------------- | -------------------------------------- |
| CRUD operations        | Create, Read, Update, Delete tasks     |
| Database integration   | Uses MySQL with `database/sql`         |
| Server-side rendering  | HTML templates for UI                  |
| Lightweight backend    | Simple and efficient Go server         |
| Deployment-ready setup | Supports Docker and Nife.io deployment |

---

## Tech Stack

| Technology     | Purpose              |
| -------------- | -------------------- |
| Go             | Runtime environment  |
| MySQL          | Database             |
| database/sql   | Database interaction |
| HTML Templates | UI rendering         |
| Docker         | Container packaging  |
| Nife.io        | Deployment platform  |

---

## Prerequisites

Before running the project locally, make sure the following are installed.

| Requirement | Notes                        |
| ----------- | ---------------------------- |
| Go          | Installed and configured     |
| MySQL       | Running database instance    |
| Git         | Required to clone repository |

---

## Getting Started

### Clone the repository

```bash
git clone https://github.com/ichtrojan/go-todo.git
cd go-todo
```

### Setup environment

```bash
cp .env.example .env
```

Update `.env` with your database credentials.

### Run the application

```bash
go run main.go
```

Then open the application at `http://localhost:4040`.

---

## Run with Docker

This project includes a Dockerfile for container-based execution.

### Build the image

```bash
docker build -t go-todo-list .
```

### Run the container

```bash
docker run -p 4040:4040 go-todo-list
```

After the container starts, open the app at `http://localhost:4040`.

---

## Deploy on Nife.io

You can deploy this application on [Nife.io][1] using either a Docker image, the source repository, or the CLI.[1][2]

### Option 1: Deploy from a Docker image

First, build and push the image to your preferred container registry.

```bash
docker build -t go-todo-list .
docker tag go-todo-list <username>/go-todo-list:latest
docker push <username>/go-todo-list:latest
```

Then configure a new application in Nife.io with the following settings.

| Setting            | Value                                    |
| ------------------ | ---------------------------------------- |
| Source             | Docker Image                             |
| Registry           | Docker Hub or another supported registry |
| Image              | `<username>/go-todo-list:latest`         |
| Internal Port      | `4040`                                   |
| External Port      | `80`                                     |
| Suggested Replicas | `1`                                      |

### Option 2: Deploy from the Git repository

You can also deploy the project directly from GitHub.

| Setting       | Value                       |
| ------------- | --------------------------- |
| Source        | Git Repository              |
| Provider      | GitHub                      |
| Branch        | `main`                      |
| Internal Port | `4040`                      |
| External Port | `80`                        |
| Build Mode    | Auto-Dockerize with runtime |

### Option 3: Deploy with `nifectl`

If you prefer the command line, use the following workflow.

```bash
nifectl auth login
nifectl init
nifectl deploy
```

For step-by-step instructions, see the [Nife.io Quick Deploy documentation][2] and the [nifectl quick start guide][4].

---

## Environment Variables

The following variables are commonly relevant for deployment.

| Variable | Description       | Example     |
| -------- | ----------------- | ----------- |
| DB_HOST  | Database host     | `localhost` |
| DB_USER  | Database username | `root`      |
| DB_PASS  | Database password | `password`  |
| DB_NAME  | Database name     | `todo_db`   |
| PORT     | Application port  | `4040`      |

---

## Repository Structure

| Path         | Purpose                      |
| ------------ | ---------------------------- |
| `main.go`    | Application entry point      |
| `.env`       | Environment configuration    |
| `templates/` | HTML templates               |
| `Dockerfile` | Container build instructions |
| `go.mod`     | Dependency management        |

---

## Troubleshooting

| Issue                       | Suggested fix                 |
| --------------------------- | ----------------------------- |
| Port already in use         | Change port or stop process   |
| MySQL connection fails      | Verify DB credentials         |
| App not starting            | Check logs and `.env`         |
| Go not installed            | Install Go and verify         |
| Docker build fails          | Verify Dockerfile             |
| Deployment fails on Nife.io | Check ports and configuration |
| App not accessible          | Verify routing and logs       |

---

## Acknowledgements

This repository is maintained by **Nifetency** as a sample deployment project for [Nife.io](https://nife.io).

If this repository is derived from an earlier template or upstream example, it is good practice to retain visible credit to the original author or source repository.
---

## License

This project is licensed under the MIT License.

---

## References

[1]: https://nife.io "Nife.io"
[2]: https://docs.nife.io/overview/quick-deploy "Nife.io Quick Deploy"
[3]: https://github.com/ichtrojan/go-todo "ichtrojan/go-todo"
[4]: https://docs.nife.io/Quick-Start/Nifectl "Nifectl Quick Start"
