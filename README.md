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

## Requests Flow (step-by-step)

1.  Browser → VM: you open http://192.168.178.133/
      - HTTP request to VM IP:80. Host header is "192.168.178.133".
2. Host port 80 → Traefik container
     - Docker maps the VM’s port 80 to Traefik (compose: ports: - 80:80).
3. Traefik routes the request (based on labels)
     - Traefik checks the router rules (Host/Path) and proxies the request to the container/service (client or backend).
4. Frontend served to browser
     - If the client is a dev server (Vite/react-scripts) or static files behind Traefik, the browser receives the frontend assets.
5. Browser calls backend API (e.g. fetch('/api/todos') or fetch('http://192.168.178.133/api/todos'))
     - This request again goes to Traefik, which routes to the backend container because of the PathPrefix /api.
6. Backend → MySQL (internal Docker network)
     - The backend container uses its env var (MYSQL_HOST=mysql) and connects to MySQL by hostname mysql. This resolves inside Docker to the MySQL container IP because all services are attached to the same Docker network.
    - No exposure of MySQL port 3306 to the host is required for the backend to connect.


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

## Output

![alt text](image.png)


## Tearing it down

When you're done, simply remove the containers by running the following command:

```bash
docker compose down
```
