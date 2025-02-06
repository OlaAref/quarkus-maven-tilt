# Quarkus Maven Tilt Example

This repository provides an example of how to set up a Quarkus application using Maven as the build tool and Tilt for local development. The project demonstrates how to streamline the development process by enabling fast feedback loops with live reloading and Kubernetes-native development.

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Using Tilt for Development](#using-tilt-for-development)

## Introduction

Quarkus is a Kubernetes-native Java framework tailored for GraalVM and HotSpot, designed to optimize Java for containerized environments. This project combines Quarkus with Maven for dependency management and Tilt to simplify the development workflow in Kubernetes.

Tilt automates the build, push, and deploy process, allowing developers to focus on writing code while Tilt handles the rest. This setup is ideal for local development with Kubernetes, providing fast feedback loops and live reloading.
## Prerequisites

Before you begin, ensure you have the following installed:

- Java JDK 21 or later
- [Maven](https://maven.apache.org/install.html)
- [Docker](https://docs.docker.com/get-docker/)
- [Tilt](https://docs.tilt.dev/install.html)
- A Kubernetes cluster (e.g., [Minikube](https://minikube.sigs.k8s.io/docs/), Docker Desktop, or any other cluster)

## Getting Started

1. **Clone the repository:**

   ```bash
   git clone https://github.com/OlaAref/quarkus-maven-tilt.git
   cd quarkus-Maven-tilt
    ```
2. **Build the Quarkus application:**

   ```bash
   mvn clean package
   ```
3. **Run the application locally:**

   ```bash
    mvn quarkus:dev
    ```
   This will start the Quarkus application in development mode with live reloading.
4. **Deploy to Kubernetes using Tilt:**
   Ensure your Kubernetes cluster is running and kubectl is configured to connect to it. Start Tilt:

   ```bash
   tilt up
   ```
   Tilt will automatically build the Docker image, push it to your local registry, and deploy the application to your Kubernetes cluster.
   You can monitor the progress in the Tilt web UI (usually accessible at http://localhost:10350).

## Project Structure
The project is structured as follows:

   ```sh
   └── quarkus-maven-tilt/
        ├── card
        │   ├── .dockerignore
        │   ├── .gitignore
        │   ├── .mvn
        │   ├── k8s-local.yaml
        │   ├── mvnw
        │   ├── mvnw.cmd
        │   ├── pom.xml
        │   └── src
        ├── local
        │   ├── Tiltfile
        │   ├── k8s-oracle.yaml
        │   └── k8s-shared-environment.yaml
        └── pom.xml
```
## Using Tilt for Development
Tilt simplifies the development workflow by automating the build and deployment process. When you run tilt up, Tilt will:
1. Build the Docker image for your application.
2. Push the image to your local Docker registry.
3. Deploy the application to your Kubernetes cluster.
4. Monitor changes in your code and automatically rebuild and redeploy the application.