1. Run updated [spring-practice-auth-server] with explicit [hostname] for providing a consistent hostname to link with:

```shell
docker run -d --name spring-practice-auth-server -h spring-practice-auth-server -p 9000:9000 spring-practice-auth-server:0.0.1-SNAPSHOT
```

2. Run updated [spring-practice-gateway] linked with [spring-practice-auth-server] Docker image:

```shell
docker run -d --name spring-practice-gateway --link spring-practice-auth-server:spring-practice-auth-server -p 8080:8080 spring-practice-gateway:0.0.1-SNAPSHOT --spring.profiles.active=docker
```

3. Run [spring-practice-gateway] linking with [spring-practice-auth-server] and [spring-practice-restmvc]:

```shell
docker stop spring-practice-auth-server
docker stop spring-practice-auth-gateway
docker stop spring-practice-auth-restmvc

docker rm spring-practice-auth-server
docker rm spring-practice-gateway
docker rm spring-practice-restmvc

docker run -d --name spring-practice-auth-server -h spring-practice-auth-server -e JWT-ISSUER-HOST=spring-practice-auth-server -p 9000:9000 spring-practice-auth-server:0.0.1-SNAPSHOT
docker run --name spring-practice-restmvc -d -e DB_HOST_ADDRESS=host.docker.internal -e SERVER_PORT=8080 -p 8081:8080 --link spring-practice-auth-server:spring-practice-auth-server -e SPRING_SECURITY_OAUTH2_RESOURCESERVER_JWT_ISSUER_URI=http://spring-practice-auth-server:9000 spring-practice-restmvc:0.0.1-SNAPSHOT --spring.profiles.active=localdb
docker run -d --name spring-practice-gateway --link spring-practice-auth-server:spring-practice-auth-server --link spring-practice-restmvc:spring-practice-restmvc -p 8080:8080 spring-practice-gateway:0.0.1-SNAPSHOT --spring.profiles.active=docker
```

4. Pull and run MySQL Docker image and rerun [spring-practice-restmvc] with MySQL docker database:

```shell
docker pull mysql:latest
docker run --name my-mysql-db -h my-mysql-db -d -e MYSQL_USER=restadmin -e MYSQL_PASSWORD=password -e MYSQL_DATABASE=restdb -e MYSQL_ROOT_PASSWORD=password -p 3306:3306 mysql:latest
docker run --name spring-practice-restmvc -d -e DB_HOST_ADDRESS=my-mysql-db -e SERVER_PORT=8080 -p 8081:8080 --link my-mysql-db:my-mysql-db --link spring-practice-auth-server:spring-practice-auth-server -e SPRING_SECURITY_OAUTH2_RESOURCESERVER_JWT_ISSUER_URI=http://spring-practice-auth-server:9000 spring-practice-restmvc:0.0.1-SNAPSHOT --spring.profiles.active=localdb
```