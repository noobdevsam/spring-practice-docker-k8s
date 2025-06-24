# Docker Commands

Use Spring Boot Maven Plugin to build a Docker image:

```shell
./mvnw clean package spring-boot:build-image
```

Inspect the Docker image:

```shell
docker image inspect docker.io/library/spring-practice-gateway:0.0.1-SNAPSHOT
```

Run the Docker image:

```shell
docker run spring-practice-gateway:0.0.1-SNAPSHOT
```

Run the Docker image with port mapping:

```shell
docker run -p 8080:8080 spring-practice-gateway:0.0.1-SNAPSHOT
```

Run the Docker image in background:

```shell
docker run -d -p 8080:8080 spring-practice-gateway:0.0.1-SNAPSHOT
```

List running Docker containers:

```shell
docker ps
```

Tap into a background running Docker container:

```shell
docker logs -f <container_id>
```

Stop a running Docker container:

```shell
docker stop <container_id>
```

Name and Run the Docker image in background:

```shell
docker run --name spring-practice-gateway -d -p 8080:8080 spring-practice-gateway:0.0.1-SNAPSHOT
```

Stop a running Docker container by name:

```shell
docker stop spring-practice-gateway
```

Restart a stopped Docker container by name. This will restore using the previous settings.

```shell
docker start spring-practice-gateway
```