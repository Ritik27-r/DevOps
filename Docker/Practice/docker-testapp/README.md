# docker-testapp
# Dockerizing a Node.js Application

## Overview

This project was created as part of my Docker learning journey. Instead of building a Node.js application from scratch, I cloned an existing Node.js project and focused on containerizing it using Docker and Docker Compose.

The goal was to understand how Docker packages applications, manages containers, and enables communication between multiple services.

## What I Learned

During this project, I learned how to:

* Create a Docker image using a `Dockerfile`
* Run a Node.js application inside a Docker container
* Build and manage multiple containers using Docker Compose
* Connect a Node.js application with MongoDB using Docker networking
* Use volumes to persist MongoDB data outside the container
* Configure environment variables for application and database services
* Expose container ports to the host machine
* Understand the difference between images, containers, volumes, and networks

## Tech Stack

* Node.js
* Express.js
* MongoDB
* Mongo Express
* Docker
* Docker Compose

## Project Structure

```text
.
├── Dockerfile
├── docker-compose.yml
├── server.js
├── package.json
├── .gitignore
└── db/
```

> **Note:** The `db` directory is used as a bind mount for MongoDB data and is ignored by Git.

## Running the Project

### Build and start the containers

```bash
docker compose up --build
```

### Run in detached mode

```bash
docker compose up -d
```

### Stop the containers

```bash
docker compose down
```

## Docker Concepts Practiced

### Dockerfile

Created a custom Docker image for the Node.js application by:

* Selecting a Node.js base image
* Copying the application source code
* Setting environment variables
* Running the application inside the container

### Docker Compose

Used Docker Compose to manage multiple services:

* Node.js application
* MongoDB
* Mongo Express

This made it possible to start the complete development environment with a single command.

### Volumes

Configured Docker volumes to persist MongoDB data on the host machine, ensuring the database remains intact even if the container is removed.

### Networks

Learned how Docker Compose automatically creates a bridge network, allowing containers to communicate using their service names. For example, the Node.js application can connect to MongoDB using the hostname:

```text
mongo:27017
```

instead of using `localhost`.

## Note

The original Node.js application was cloned from an existing repository. My primary focus in this project was learning Docker concepts by containerizing the application and configuring Docker Compose, networking, and persistent storage.

