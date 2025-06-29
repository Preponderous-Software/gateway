# Preponderous Software Gateway
A microservices gateway infrastructure using Traefik for routing and service discovery. This project provides a scalable foundation for Preponderous Software's microservices architecture.
## Features
- Traefik reverse proxy with automatic routing
- HTTPS support with automatic certificate management
- Docker-based deployment for easy scaling
- Example services ready for customization

## Project Structure
- **config/**: Configuration files
   - **traefik/**: Traefik configuration files
   - **ssl/**: SSL certificates and related files
- **services/**: Microservices
   - **app1/**: Sample microservice application
   - **whoami/**: Simple diagnostic service
- **compose.yml**: Main Docker Compose configuration
## Requirements
- Docker and Docker Compose
- Git

## Getting Started
### Installation
1. Clone the repository:
``` 
   git clone https://github.com/preponderous-software/gateway.git
   cd gateway
```
1. Create an empty file for SSL certificates and set proper permissions
``` 
   mkdir -p config/ssl touch config/ssl/acme.json chmod 600 config/ssl/acme.json
```
### Running Locally
1. Start the entire stack with Docker Compose:
``` 
   docker compose up -d
```
1. Access the services:
    - Traefik Dashboard: [http://traefik.localhost:8080](http://traefik.localhost:8080)
    - Whoami Service: [http://whoami.localhost](http://whoami.localhost)
    - App1: [http://app1.localhost](http://app1.localhost)

### Development
To modify or add services:
1. Edit the file to add new services `compose.yml`
2. Use the existing services as templates for Traefik integration
3. Build and deploy using Docker Compose

## Configuration
- `config/traefik/traefik.yml`: Main Traefik configuration
- `config/traefik/dynamic.yml`: Dynamic Traefik configuration for middleware, etc.
- `compose.yml`: Docker Compose service definitions

## Adding a New Service
1. Create a new directory for your service
2. Add the necessary Dockerfile and application files
3. Add the service to with appropriate Traefik labels `compose.yml`
4. Rebuild and restart the stack:
``` 
   docker compose down
   docker compose up -d
```
## Troubleshooting
- Check Traefik logs: `docker logs traefik`
- Ensure local DNS resolution is working for the `.localhost` domains
- Verify that the required ports (80, 443, 8080) are available on your system

## License
Copyright © 2025 Daniel McCoy Stephenson. All rights reserved.
