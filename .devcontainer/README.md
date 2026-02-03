# GitHub Codespaces Configuration

This directory contains the configuration for running CK-X Simulator in GitHub Codespaces.

## Quick Start

1. **Open in Codespaces**: Click the "Code" button on GitHub and select "Create codespace on [branch-name]"
2. **Wait for setup**: The codespace will automatically:
   - Install Node.js 20
   - Set up Docker and Docker Compose
   - Install kubectl and helm
   - Install npm dependencies for app and facilitator services
3. **Start the simulator**: Run `./compose-deploy.sh` or use docker-compose:
   ```bash
   docker-compose up -d
   ```
4. **Access the application**: The simulator will be available on port 30080 (automatically forwarded)

## What's Included

- **Base Image**: Node.js 20 (Debian Bullseye)
- **Docker**: Docker-in-Docker for running containers
- **Kubernetes Tools**: kubectl and helm
- **VS Code Extensions**:
  - Docker extension for container management
  - Kubernetes extension for cluster interaction
  - ESLint and Prettier for code quality

## Configuration Details

The `devcontainer.json` file configures:
- **Features**: Docker-in-Docker, Kubernetes tools, Git
- **Port Forwarding**: Port 30080 (Nginx reverse proxy)
- **Post-Create**: Automatic npm install for app and facilitator
- **Privileged Mode**: Required for Docker-in-Docker and KIND cluster

## Running the Simulator

After the codespace is created, you can start the CK-X Simulator:

```bash
# Using the deploy script
./compose-deploy.sh

# Or manually with docker-compose
docker-compose up -d

# Check status
docker-compose ps

# View logs
docker-compose logs -f
```

The application will be accessible through the forwarded port 30080.

## Stopping the Simulator

```bash
docker-compose down
```

## Notes

- The codespace runs with sufficient resources to handle the multi-service Docker setup
- Docker-in-Docker is required for the KIND Kubernetes cluster
- All services defined in `docker-compose.yaml` will run in the codespace
