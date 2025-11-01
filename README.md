<div style="display: flex; align-items: center; gap: 10px;">
  <img src="https://skillicons.dev/icons?i=react,vite,nodejs,php,mysql" style="height: 40px;"/>
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/traefikproxy/traefikproxy-original.svg" style="height: 40px;"/> 
</div>

# React PHP Todo App

This repository provides a complete, modern development environment built with Docker Compose. It features a React/Node.js application served via a Traefik reverse proxy, uses Vite for fast frontend hot-reloading, and persists data with a MySQL container, showcasing robust, multi-service container orchestration.

## Application Architecture

![image](https://github.com/docker/getting-started-todo-app/assets/313480/c128b8e4-366f-4b6f-ad73-08e6652b7c4d)


This is a React/Node.js/MySQL starter application designed around Docker best practices. The architecture includes:

- Vite: Used for rapid, hot-reloading development in the frontend container.

- MySQL: The containerized relational database for persistence.

- Traefik: Acts as the cluster-level reverse proxy and load balancer, managing traffic to the application services.

## Development

To spin up the project, simply install Docker Desktop and then run the following 
commands:

```bash
git clone https://github.com/mirakib/react-mysql-to-do-app.git
```

```bash
cd react-mysql-to-do-app
```

```bash
docker compose up -d
```


## Tearing it down

When you're done, simply remove the containers by running the following command:

```bash
docker compose down
```
