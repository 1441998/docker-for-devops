
# Docker Fundamentals - Notes

## Introduction to Docker

- **What is Docker?**  
  Docker is a platform that simplifies the development, deployment, and operation of applications by using containerization. Containers allow developers to package applications with all of their dependencies, ensuring they run consistently across various environments.

- **Why Use Docker?**  
  Docker ensures that applications can be developed, tested, and deployed with consistency across different environments, avoiding the common issue of "it works on my machine." It simplifies CI/CD workflows, enhances resource efficiency, supports microservices architectures, and enables fast, scalable deployments.

- **How Docker Works**  
  Docker uses a client-server architecture. The Docker client sends commands (like building images or running containers) to the Docker daemon, which manages containers and images. Docker images are read-only templates, and containers are instances of those images that run the applications.

## Virtualization vs. Containerization

- **Virtualization**: Virtual machines (VMs) emulate entire physical machines, each with its own OS, consuming more resources (RAM, CPU) and leading to slower performance compared to containers.

- **Containerization**: Containers share the host system’s OS kernel and run as isolated processes. This approach is more efficient in terms of system resource usage and offers faster startup times compared to VMs.

## Basic Docker Commands

1. **Check Docker version**  
   Command: `docker --version`  
   This command displays the installed version of Docker, which helps ensure that your environment is up-to-date or compatible with your needs.

2. **List running containers**  
   Command: `docker ps`  
   Lists all containers currently running on the system. It provides information like container ID, image used, and status.

3. **List all containers (including stopped)**  
   Command: `docker ps -a`  
   This lists all containers, whether running or stopped, and provides additional details such as when the container was created and exited.

4. **Pull an image from Docker Hub**  
   Command: `docker pull [image_name]`  
   Downloads a Docker image from Docker Hub (a public image repository) and stores it locally.

5. **Run a container**  
   Command: `docker run [image_name]`  
   Runs a container from the specified image. If the image is not available locally, Docker will pull it from Docker Hub.

6. **Build an image from a Dockerfile**  
   Command: `docker build -t [image_name] .`  
   This command builds a Docker image from a Dockerfile in the current directory and tags it with the specified name.

7. **Kill a running container**  
   Command: `docker kill [container_name/ID]`  
   Forces the termination of a running container. This is useful for unresponsive containers.

8. **Remove a stopped container**  
   Command: `docker rm [container_name/ID]`  
   Deletes a stopped container from the system, freeing up disk space and resources.

## Dockerfile and Automation

- **Dockerfile**:  
  A Dockerfile is a script that contains a series of instructions to build a Docker image. It defines everything needed to create an image, from the base image to the application code and dependencies.

### Breakdown of Dockerfile Contents:

```Dockerfile
# Use an official Node.js runtime as the base image
FROM node:14

# Set the working directory in the container
WORKDIR /app

# Copy the package.json file to the working directory
COPY package.json .

# Install the dependencies
RUN npm install

# Copy the remaining application files to the container
COPY . .

# Expose the port the app will run on
EXPOSE 3000

# Start the application
CMD ["node", "index.js"]
```

#### Explanation:

1. **FROM node:14**  
   This line specifies the base image from which the Docker image will be built. In this case, the official `node:14` image from Docker Hub, which includes Node.js v14, is used as the starting point. The base image provides the runtime environment for the container.

2. **WORKDIR /app**  
   This instruction sets the working directory for any subsequent commands. It creates the `/app` directory inside the container if it doesn’t exist, and all subsequent file operations will happen within this directory.

3. **COPY package.json .**  
   This copies the `package.json` file from the local file system to the container’s working directory (`/app`). This file contains the list of dependencies for a Node.js application.

4. **RUN npm install**  
   The `RUN` instruction executes a command during the image build process. Here, it runs `npm install` to install the dependencies listed in `package.json`. The installed dependencies are saved inside the container image.

5. **COPY . .**  
   This command copies all the application files from the current directory (on the host) to the container's working directory (`/app`). This includes the source code for the application.

6. **EXPOSE 3000**  
   This exposes port 3000 to be used by the application. It tells Docker that the container will be listening on this port, which is essential for web applications so that traffic can be routed to the correct port.

7. **CMD ["node", "index.js"]**  
   The `CMD` instruction specifies the command to run when the container starts. Here, it runs `node index.js` to start the Node.js application. Unlike `RUN`, which is executed during the image build process, `CMD` runs when the container is launched.

## Practice Platform Suggestions

- **Local Environment**:  
  Install Docker on your personal system (Windows, macOS, or Linux) and practice running containers, building Dockerfiles, and managing images. This is the most hands-on method and gives you full control over your setup.

- **Cloud Platforms**:  
  Use platforms like AWS, Microsoft Azure, or Google Cloud to spin up virtual machines and practice Docker commands in a scalable cloud environment. Many cloud providers offer Docker-ready environments or pre-configured images to speed up development.

- **Online Docker Labs**:  
  Browser-based platforms such as **Play with Docker** and **Katacoda** allow you to practice Docker without installing it locally. These online labs provide interactive environments with guided tutorials, allowing you to quickly experiment with Docker in a controlled setting.

