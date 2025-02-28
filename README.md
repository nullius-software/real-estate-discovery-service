# Real Estate Discovery Service - Setup Guide

## About This Repository

The `real-estate-discovery-service` repository serves as the Discovery Service for the Real Estate project. The Discovery Service, powered by Kotlin and SpringBoot, connects all the microservices in the Real Estate project using Eureka for service discovery. This ensures that each microservice can dynamically locate and communicate with other microservices.

## Prerequisites

- Docker: Ensure Docker is installed and running on your machine. Download from [docker.com](https://www.docker.com) if needed.
- Access to a terminal (bash, cmd, PowerShell, etc.).
- Internet connection to pull necessary images.
- Keycloak: Ensure Keycloak is running locally. The guide for configuring Keycloak locally can be found [here](https://github.com/nullius-software/real-estate-keycloak-render).

## Step 1: Clone the Repository

First, clone the `real-estate-discovery-service` repository to your local machine:

```bash
git clone https://github.com/nullius-software/real-estate-discovery-service.git
cd real-estate-discovery-service
```

## Step 2: Build the Docker Image

Build the Docker image for the discovery service:

```bash
docker build -t real-estate-discovery-service .
```

## Step 3: Run the Docker Container

Run the Docker container for the discovery service:

```bash
docker run -p 8761:8761 real-estate-discovery-service
```

### Explanation:

- `-p 8761:8761`: Maps port 8761 from the container to your local machine.

Wait for the container to start. You’ll see logs indicating the discovery service is ready when something like this appears:

```
Started DiscoveryServiceApplication in X.XXX seconds
```

## Step 4: Access the Discovery Service Dashboard

Open your browser and go to: [http://localhost:8761](http://localhost:8761).

You should see the Eureka dashboard indicating that the discovery service is running.

## Step 5: Verify the Configuration

Ensure that the other microservices in the Real Estate project are configured to register with the discovery service by checking their configuration files. They should have the Eureka server URL set to `http://localhost:8761/eureka`.
