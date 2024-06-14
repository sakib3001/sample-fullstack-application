# Sample Fullstack Application
Welcome to the Full Stack Sample Todo App! This application allows users to manage their tasks with ease. The project is built with a modern tech stack, including Next.js for the frontend and Node.js, Express, PostgreSQL, and Redis for the backend.

## Prerequisites
Before you begin, ensure you have the following tools installed on your machine:
- [Docker Engine](https://docs.docker.com/engine/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Setup
### Environment File Configuration
To run the App you need to modify  `sample.env` in the root of your project directory with the following content:

#### sample.env
```env
# backend
DATABASE_URL=postgresql://<Username>:<Password>@db:5432/todo
REDIS_URL=redis://redis:6379

# db (postgres)
POSTGRES_USER=<Username>
POSTGRES_PASSWORD=<Password>
POSTGRES_DB=todo

```
## Run The App Locally 

- #### Clone the project

```bash
  git clone -b my-task https://github.com/sakib3001/sample-fullstack-application.git

```

- #### Go to the project directory

```bash
 cd sample-fullstack-application
```

- #### Start the App

```bash
  docker compose up -d --build
```


## Access The App

To access the todo app open your browser and type: 

```bash
  http://localhost:8080/
```

## Stop The App
 
#### Stop All the containers in the docker-compose.yml
```bash
  docker compose stop
```
#### To release all the resources 
```bash
  docker compose down
```

## Remarks

- ##### Healthchecks for the `db` and the `redis` is not added to the compose file.
- ##### In some cases, volume binding is crucial for data persistence. Here, I had used the `./pgdata` directory for data persistence. Alternatively, Docker volumes could be used, but for replication purposes, I prefer `volume binding`. For the ease of the project structure here I am using `pgdata` docker volume right now.


