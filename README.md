# Docker Web Dev Environment
A development environment with PHP, NodeJS, Python3 as server and Mariadb and PostgreSQL as database.

## Quickstart

### 1. Set up network
Create a docker network to connect all of the containers. In this case it's called `genesis`. Of course you can rename it to anything. Just replace the word `genesis` to your desire.

### 2. Build and run
Navigate to each directory with `Dockerfile` or `docker-compose.yml`, or both files in it and run on terminal:
```
docker-compose build && docker-compose up -d
```
or to display the logs:
```
docker-compose build && docker-compose up -d && docker-compose logs -f
```
