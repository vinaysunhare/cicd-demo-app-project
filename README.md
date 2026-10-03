# CI/CD Demo App

A simple FastAPI web application that can be run locally using Docker.

## Prerequisites

Before running the application, make sure you have:

- Git installed
- Docker installed and running

You can verify Docker with:

```bash
docker --version
```

---

## Run the Application Locally

### 1. Clone the Repository

```bash
git clone https://github.com/vinaysunhare/cicd-demo-app-project.git
```

Go to the project directory:

```bash
cd cicd-demo-app-project
```

---

### 2. Build the Docker Image

Run the following command from the project directory:

```bash
docker build -t cicd-demo-app .
```

This will:

- Read the `Dockerfile`
- Install Python dependencies
- Copy the application code
- Create a Docker image named `cicd-demo-app`

---

### 3. Run the Docker Container

```bash
docker run -d --name cicd-demo-app -p 8000:8000 cicd-demo-app
```

The application will now be running inside a Docker container.

---

### 4. Open the Application

Open your browser and visit:

```text
http://localhost:8000
```

The application should now be visible.

---
<img width="1611" height="957" alt="image" src="https://github.com/user-attachments/assets/4090fce6-066f-49c3-8a66-15ce4966e6a2" />

## Check the Application

You can check whether the container is running with:

```bash
docker ps
```

You should see the port mapping:

```text
0.0.0.0:8000->8000/tcp
```

You can also check the application health endpoint:

```text
http://localhost:8000/health
```
<img width="1608" height="758" alt="image" src="https://github.com/user-attachments/assets/9dcc93f3-ed20-4d0f-9b80-88a8362abc4e" />

Expected response:

```json
{
  "status": "healthy"
}
```

---

## View Application Logs

If the application does not open correctly, check the container logs:

```bash
docker logs cicd-demo-app
```

To continuously view the logs:

```bash
docker logs -f cicd-demo-app
```

---

## Stop the Application

To stop the running container:

```bash
docker stop cicd-demo-app
```

---

## Start the Application Again

If the container already exists and was only stopped:

```bash
docker start cicd-demo-app
```

Then open:

```text
http://localhost:8000
```

---

## Remove the Container

If you want to remove the container completely:

```bash
docker rm -f cicd-demo-app
```

After removing it, you can create it again using:

```bash
docker run -d --name cicd-demo-app -p 8000:8000 cicd-demo-app
```

---

## Rebuild After Code Changes

If you make changes to the application code, rebuild the Docker image:

```bash
docker build -t cicd-demo-app .
```

Then remove the old container:

```bash
docker rm -f cicd-demo-app
```

And run the new container:

```bash
docker run -d --name cicd-demo-app -p 8000:8000 cicd-demo-app
```

---

## Project Structure

```text
cicd-demo-app-project/
│
├── app/
│   └── main.py
│
├── templates/
│   └── index.html
│
├── Dockerfile
├── requirements.txt
├── .dockerignore
└── README.md
```

---

## Port

The application runs on:

```text
8000
```

Docker maps:

```text
localhost:8000 → container:8000
```

Application URL:

```text
http://localhost:8000
```

Health check:

```text
http://localhost:8000/health
```

---

## Quick Start

If Docker is already installed and running, you can run the complete setup with:

```bash
git clone https://github.com/vinaysunhare/cicd-demo-app-project.git
cd cicd-demo-app-project
docker build -t cicd-demo-app .
docker run -d --name cicd-demo-app -p 8000:8000 cicd-demo-app
```

Then open:

```text
http://localhost:8000
```
<img width="1611" height="957" alt="image" src="https://github.com/user-attachments/assets/4090fce6-066f-49c3-8a66-15ce4966e6a2" />
