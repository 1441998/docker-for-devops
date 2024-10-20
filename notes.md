
# Docker Fundamentals - Notes

## Introduction to Docker
- **What is Docker?**
  Docker is a platform designed to simplify the development, deployment, and running of applications inside containers. Containers are lightweight, portable, and provide a consistent environment for application execution.

- **Why use Docker?**
  Docker allows you to package an application and its dependencies into a container, ensuring consistency across multiple development and production environments. It's efficient for CI/CD pipelines, and helps in microservices architecture, scalability, and rapid deployment.

- **How Docker Works:**
  Docker uses a client-server architecture. The Docker daemon runs on the host machine, and the Docker client allows users to interact with it. Docker images are used to create containers.

## Key Differences: Virtualization vs. Containerization
- **Virtualization**: A virtual machine (VM) emulates a complete physical machine. This includes its own OS, and requires more resources than containers.
- **Containerization**: Containers run on the host OS kernel, sharing resources efficiently. They are faster, more lightweight, and isolated compared to VMs.

## Basic Docker Commands

1. **Check Docker version**:  
   `docker --version`
   - This command shows the installed Docker version.

2. **List running containers**:  
   `docker ps`
   - This command lists all currently running containers.

3. **List all containers (including stopped)**:  
   `docker ps -a`
   - This command shows all containers, including those that have stopped.

4. **Pull an image**:  
   `docker pull [image_name]`
   - This command pulls the specified image from Docker Hub.

5. **Run a container**:  
   `docker run [image_name]`
   - This command runs a container from the specified image.

6. **Build an image from a Dockerfile**:  
   `docker build -t [image_name] .`
   - This command builds a Docker image from a Dockerfile located in the current directory.

7. **Kill a running container**:  
   `docker kill [container_name/ID]`
   - This command forcibly stops a running container.

8. **Remove a container**:  
   `docker rm [container_name/ID]`
   - This command removes a stopped container.

## Additional Docker Concepts:
- **Dockerfile**: A Dockerfile is a script containing instructions on how to build a Docker image. It defines what goes into the image, such as the base OS, dependencies, and application files.

## Practice Environment:
Commands were practiced on both:
- **Windows**: Installed Docker Hub and ran basic commands.
- **AWS EC2 (Ubuntu)**: Ran the same Docker commands on an EC2 instance to explore Docker in a cloud environment.
