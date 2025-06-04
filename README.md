This project consists of a Node.js frontend with MongoDB database and Python FastAPI backend, all containerized for development and production.

## Production Deployment

To deploy the complete system in production using Docker:

```bash
# Clone the repository
git clone <repository-url>
cd personal-chat-project

# Initialize submodules (if using langfuse)
git submodule update --init --recursive --force

git submodule foreach git checkout main && git submodule update --recursive

# Build and start all services
docker compose up -d

# Check if all services are running
docker compose ps

# View logs if needed
docker compose logs -f
```

The system will be available at:
- Frontend (UI): http://localhost:3010
- Backend API: http://localhost:8010
- MongoDB: localhost:27020

To stop the services:
```bash
docker compose down
```

To rebuild after code changes:
```bash
docker compose down
docker compose up --build -d
```

## How tu run

```bash

git submodule update --init --recursive

docker compose up db -d


```

## How tu run in dev mode

```bash

#first, run the database
docker compose up db -d

#second, run langfuse
cd langfuse 
docker compose up -d

#third, run AI project
# open folder in dev container

#fourth, run UI project
# open folder in dev container

```


## Langfuse setup

For Langfuse to work in the same network, I needed to put this in the docker-compose.yml file

```yml
networks:
  app-network:
    external: true
    name: personal-chat-project_app-network
```