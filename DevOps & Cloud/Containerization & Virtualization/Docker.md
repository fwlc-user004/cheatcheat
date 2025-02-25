# 🐳 Docker Cheatsheet

## 🔹 Installation & Setup
```sh
# Install Docker (Linux/macOS)
sudo apt install docker.io  # Ubuntu/Debian
brew install docker         # macOS

# Verify installation
docker --version
```

## 🔹 Docker Basics
```sh
# Check Docker info
docker info

# List all running containers
docker ps

# List all containers (including stopped ones)
docker ps -a

# List all images
docker images
```

## 🔹 Working with Containers
```sh
# Run a container
docker run -d -p 8080:80 nginx

# Start a stopped container
docker start container_id

# Stop a running container
docker stop container_id

# Remove a container
docker rm container_id
```

## 🔹 Working with Images
```sh
# Pull an image from Docker Hub
docker pull ubuntu

# Remove an image
docker rmi image_id

# Build an image from Dockerfile
docker build -t my-image .
```

## 🔹 Docker Volumes
```sh
# Create a volume
docker volume create my_volume

# List volumes
docker volume ls

# Attach a volume to a container
docker run -d -v my_volume:/data nginx
```

## 🔹 Docker Networks
```sh
# List networks
docker network ls

# Create a network
docker network create my_network

# Connect a container to a network
docker network connect my_network container_id
```

## 🔹 Docker Compose
```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
```
```sh
# Start services
docker-compose up -d

# Stop services
docker-compose down
```

## 🔹 Debugging & Logs
```sh
# Show container logs
docker logs container_id

# Check running processes inside a container
docker top container_id

# Open an interactive shell inside a container
docker exec -it container_id /bin/sh
```

## 🔹 Docker Best Practices
- Use **multi-stage builds** for smaller image sizes.
- Prefer **alpine-based images** for lightweight containers.
- Use **named volumes** instead of anonymous ones.
- Minimize **layers** in Dockerfiles for better performance.
- Keep **secrets & credentials** out of Docker images.

---