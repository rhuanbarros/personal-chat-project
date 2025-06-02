This project consists of a Node.js frontend with MongoDB database and Python FastAPI backend, all containerized for development.

## How tu run

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