1. Run updated [spring-practice-auth-server] Docker image:

```shell
docker run -d --name spring-practice-auth-server -h spring-practice-auth-server -p 9000:9000 spring-practice-auth-server:0.0.1-SNAPSHOT
```

2. Run updated [spring-practice-gateway] Docker image:

```shell
docker run -d --name spring-practice-gateway --link spring-practice-auth-server:spring-practice-auth-server -p 8080:8080 spring-practice-gateway:0.0.1-SNAPSHOT --spring.profiles.active=docker
```

3. Run [spring-practice-gateway] linking with [spring-practice-auth-server] and [spring-practice-restmvc]:

```shell
docker stop spring-practice-gateway
docker rm spring-practice-gateway
docker run -d --name spring-practice-gateway --link spring-practice-auth-server:spring-practice-auth-server --link spring-practice-restmvc:spring-practice-restmvc -p 8080:8080 spring-practice-gateway:0.0.1-SNAPSHOT --spring.profiles.active=docker
```