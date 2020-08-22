---
parent: Docker
title: Docker Compose
---

# Docker Compose usage
{: .no_toc}

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Example of Docker services availability on Host Machine
* MySQL (Docker Host: `db:3306`) available from host machine by `localhost:3306`
* Redis (Docker Host: `cache:6379`) available from host machine by `localhost:6379`
* API (Docker Host: `api:80`) available from host machine by nginx (`web:443`) container by URL `http://api.domain.dev` or `http://domain.dev/api`
* APP (Docker Host: `app:3000`) available from host machine by nginx (`web:443`) container by URL `http://app.domain.dev` or `http://domain.dev`
All services in detailes described in `docker-compose.yaml` for each service

# Local browser configuration
1. To use access to docker services from local Browser you need to add new line to local `/etc/hosts` file:
```terminal
127.0.0.1 api.doamin.dev app.doamin.dev
```
2. Be sure that `SSL` certificates from current project already installed to your Operations system or your browser or even both places. More detail about your case of configuration you can find in HTTPS/SSL articles here

## Port blocking or port already in use
Please check and be sure that all "NON Docker" local MySQL, Redis, nginx and similar services turned off or stopped before start docker containers

Example of Ports that need to be available (NOT IN USE) before start: `80, 443, 3306, 6379` full list described in `docker-compose.yaml` for each service

# Usage examples

## Run Docker Compose

* Run all services
```terminal
$ docker-compose up
```

* Run all services in detouched (background) mode:
```terminal
$ docker-compose up -d
```

* Run only `npm install` command:
```terminal
$ docker-compose run --rm nodejs_container_name npm install
```

* Apply all migrations to docker Database:
```terminal
$ docker-compose run --rm api_container_name phinx migrate
```

* Stop all services
```terminal
$ docker-compose stop
```

* Clear state of DB and all other containers too
```terminal
$ docker-compose down
```

## Run custom command in container

* Run any command inside docker container environment:

```terminal
$ docker-compose run container_name your_terminal_command_here
```

example: 

```terminal
$ docker-compose run --rm container_name npm run update-schema
```

* Run any multiple commands inside docker environment:

```terminal
$ docker-compose run --rm container_name bash -c "your_terminal_command_1 && your_terminal_command_2 && your_terminal_command_3"
```

example: 

```terminal
$ docker-compose run --rm app_container_name bash -c "cd packages && npm run update-schema && npm run build"
```

## Run only backend

Run only API with DB and Redis:

```terminal
$ docker-compose run --rm  -d --service-ports api_container_name
```

In this case DB and Redis will start automatically by `depends_on` directive inside `docker-comose.yaml` config for `api` container.
Where:

* `--service-ports` - provide open ports to be available from Host Machine.
* `-d` - run this containers in detouched (background) mode

## Check containers

Check which containers already running and look at `healthy` status:

```terminal
$ docker-compose ps
```

## Check Containers logs

Follow logs from one of containers

```terminal
$ docker-compose logs -f container_name
```