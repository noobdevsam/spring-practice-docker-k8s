# Docker Commands

Use Spring Boot Maven Plugin to build a Docker image:

```shell
./mvnw clean package spring-boot:build-image
```

Inspect the Docker image:

```shell
docker image inspect docker.io/library/spring-practice-gateway:0.0.1-SNAPSHOT
```