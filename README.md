# Preponderous Software Gateway
A unified deployment infrastructure designed to simplify the hosting and management of Preponderous Software's service ecosystem. This project streamlines the deployment of multiple interconnected services through Docker containerization and Traefik for intelligent routing.

## Purpose
This gateway serves as a centralized deployment platform for Preponderous Software services, making it easier to:
- Deploy multiple services with a single command
- Manage routing and service discovery automatically
- Secure all services with consistent HTTPS configuration
- Scale individual services based on demand
- Simplify development and testing workflows

## Included Services
The gateway currently supports the following services:
- **Preponderous Website**: Main company website
- **Dan's Plugins Central Website**: Community hub for Minecraft plugins
- **Minecraft Server**: Preconfigured DPC Minecraft server with plugin support
- **Diagnostic Tools**: Simple services for monitoring and troubleshooting

## Technical Architecture
- **Traefik**: Handles routing, SSL termination, and service discovery
- **Docker**: Provides containerization and isolation for each service
- **Docker Compose**: Orchestrates the multi-container deployment

## Requirements
- Docker and Docker Compose
- Git

## Getting Started
### Installation
1. Clone the repository:
```
bash git clone [https://github.com/preponderous-software/gateway.git](https://github.com/preponderous-software/gateway.git) cd gateway
``` 

2. Create an empty file for SSL certificates and set proper permissions:
```
bash mkdir -p config/ssl touch config/ssl/acme.json chmod 600 config/ssl/acme.json
``` 

### Deployment
1. Start the entire service stack with a single command:
```bash
docker compose up -d
```
1. Access the services:
    - Traefik Dashboard: [http://traefik.localhost](http://traefik.localhost)
    - Preponderous Website: [http://preponderous.localhost](http://preponderous.localhost)
    - Dan's Plugins Website: [http://dansplugins.localhost](http://dansplugins.localhost)
    - Other services as configured

## Service Configuration
Each service can be configured through environment variables and Docker Compose settings:
- **Minecraft Server**: Configure plugins, operators, and server settings
- **Websites**: Adjust build parameters and runtime configurations
- **Traefik**: Modify routing rules and SSL configuration

## Adding New Services
1. Create a new directory for your service in the folder `services/`
2. Add the necessary Dockerfile and application files
3. Register the service in with appropriate Traefik labels `compose.yml`
4. Rebuild and restart the stack:
``` bash
docker compose down
docker compose up -d
```
## Troubleshooting
- Check Traefik logs: `docker logs traefik`
- Ensure local DNS resolution is working for the configured domains
- Verify that the required ports are available on your system

## License
Copyright © 2025 Daniel McCoy Stephenson. All rights reserved.
