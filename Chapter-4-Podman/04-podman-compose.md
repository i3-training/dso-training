# Multi-container Applications with Compose


In today's computing, many applications are developed as microservices. In the context of containers, every microservice is a container image, which developers manage as an independent container. Because one application is composed of several containers, it might become difficult to manage the containers as a group.

## The Compose File
The Compose file is a YAML file that contains the following sections:
- version (deprecated): Specifies the Compose version used.
- services: Defines the containers used.
- networks: Defines the networks used by the containers.
- volumes: Specifies the volumes used by the containers.
- configs: Specifies the configurations used by the containers.
- secrets: Defines the secrets used by the containers.
The secrets and configs objects are mounted as a file in the containers.

**Start and Stop Containers with Podman Compose** 

You can execute a Compose file by using the podman-compose up command, which creates the
defined objects, such as volumes or networks, and starts the defined containers.
```
git clone https://github.com/i3-training/dso-training.git
cd Chapter-4-Podman/nginx-flask-mysql/
cat compose.yml
```

```
services:
  db:
    # We use a mariadb image which supports both amd64 & arm64 architecture
    image: mariadb:10-focal
    # If you really want to use MySQL, uncomment the following line
    #image: mysql:8
    command: '--default-authentication-plugin=mysql_native_password'
    restart: always
    healthcheck:
      test: ['CMD-SHELL', 'mysqladmin ping -h 127.0.0.1 --password="$$(cat /run/secrets/db-password)" --silent']
      interval: 3s
      retries: 5
      start_period: 30s
    secrets:
      - db-password
    volumes:
      - db-data:/var/lib/mysql
    networks:
      - backnet
    environment:
      - MYSQL_DATABASE=example
      - MYSQL_ROOT_PASSWORD_FILE=/run/secrets/db-password
    expose:
      - 3306
      - 33060

  backend:
    build:
      context: backend
      target: builder
    restart: always
    secrets:
      - db-password
    ports:
      - 8000:8000
    networks:
      - backnet
      - frontnet
    depends_on:
      db:
        condition: service_healthy

  proxy:
    build: proxy
    restart: always
    ports:
      - 80:80
    depends_on: 
      - backend
    networks:
      - frontnet

volumes:
  db-data:

secrets:
  db-password:
    file: db/password.txt

networks:
  backnet:
  frontnet:
```


```
podman-compose up -d
```

The podman-compose stop command stops running containers that are defined as services.
Execute podman-compose down to stop and remove containers that are defined as services

```
podman-compose down
```
