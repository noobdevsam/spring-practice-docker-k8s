## Required images:

- `mongo:latest`
- `mysql:latest`
- `spring-practice-auth-server:0.0.1-SNAPSHOT`
- `spring-practice-restmvc:0.0.1-SNAPSHOT`
- `spring-practice-reactive:0.0.1-SNAPSHOT`
- `spring-practice-reactive-mongo:0.0.1-SNAPSHOT`
- `spring-practice-gateway:0.0.1-SNAPSHOT`

## Commands to run

- Display all resources in the default namespace:

```bash
kubectl get all -o wide
```

### Create Deployment for MongoDB:

```bash
kubectl create deployment my-mongo-db --image=mongo:latest --dry-run=client -o yaml > mongo-deployment.yaml
```

### Apply the MongoDB Deployment:

```bash
kubectl apply -f mongo-deployment.yaml
```

### Create a Service for MongoDB:

```bash
kubectl create service clusterip my-mongo-db --tcp=27017:27017 --dry-run=client -o yaml > mongo-service.yaml
```

### Apply the MongoDB Service:

```bash
kubectl apply -f mongo-service.yaml
```

Changes can be made to the MongoDB deployment and service configs before applying to include environment variables for
root password, database name, and user credentials as needed.

### View logs for MongoDB:

```bash
kubectl logs my-mongo-db-<pod-id>
```

### Delete Service and Deployment for MongoDB:

```bash
kubectl delete service my-mongo-db
kubectl delete deployment my-mongo-db
```

### Create Deployment for MySQL:

```bash
kubectl create deployment my-mysql-db --image=mysql:latest --dry-run=client -o yaml > mysql-deployment.yaml
```

### Apply the MySQL Deployment:

```bash
kubectl apply -f mysql-deployment.yaml
```

### Create a Service for MySQL:

```bash
kubectl create service clusterip my-mysql-db --tcp=3306:3306 --dry-run=client -o yaml > mysql-service.yaml
```

### Apply the MySQL Service:

```bash
kubectl apply -f mysql-service.yaml
```

Changes can be made to the MySQL deployment and service configs before applying to include environment variables for
root password, database name, and user credentials as needed.

### View logs for MySQL:

```bash
kubectl logs my-mysql-db-<pod-id>
```

### Delete Service and Deployment for MySQL:

```bash
kubectl delete service my-mysql-db
kubectl delete deployment my-mysql-db
```

### Create Deployment for Spring-Practice-Auth-Server:

```bash
kubectl create deployment spring-practice-auth-server --image=spring-practice-auth-server:0.0.1-SNAPSHOT --dry-run=client -o yaml > auth-server-deployment.yaml
```

### Apply the Spring-Practice-Auth-Server Deployment:

```bash
kubectl apply -f auth-server-deployment.yaml
```

### Create a Service for Spring-Practice-Auth-Server:

```bash
kubectl create service clusterip spring-practice-auth-server --tcp=9000:9000 --dry-run=client -o yaml > auth-server-service.yaml
```

### Apply the Spring-Practice-Auth-Server Service:

```bash
kubectl apply -f auth-server-service.yaml
```

Changes can be made to the [spring-practice-auth-server] deployment and service configs before applying to include
environment variables as needed.

### Create Deployment for Spring-Practice-RestMvc:

```bash
kubectl create deployment spring-practice-restmvc --image=spring-practice-restmvc:0.0.1-SNAPSHOT --dry-run=client -o yaml > restmvc-deployment.yaml
```

### Apply the Spring-Practice-RestMvc Deployment:

```bash
kubectl apply -f restmvc-deployment.yaml
```

### Create a Service for Spring-Practice-RestMvc:

```bash
kubectl create service clusterip spring-practice-restmvc --tcp=8080:8080 --dry-run=client -o yaml > restmvc-service.yaml
```

### Apply the Spring-Practice-RestMvc Service:

```bash
kubectl apply -f restmvc-service.yaml
```

Changes can be made to the [spring-practice-restmvc] deployment and service configs before applying to include
environment variables as needed.

### Create Deployment for Spring-Practice-Reactive:

```bash
kubectl create deployment spring-practice-reactive --image=spring-practice-reactive:0.0.1-SNAPSHOT --dry-run=client -o yaml > reactive-deployment.yaml
```

### Apply the Spring-Practice-Reactive Deployment:

```bash
kubectl apply -f reactive-deployment.yaml
```

### Create a Service for Spring-Practice-Reactive:

```bash
kubectl create service clusterip spring-practice-reactive --tcp=8080:8080 --dry-run=client -o yaml > reactive-service.yaml
```

### Apply the Spring-Practice-Reactive Service:

```bash
kubectl apply -f reactive-service.yaml
```

Changes can be made to the [spring-practice-reactive] deployment and service configs before applying to include
environment variables as needed.

### Create Deployment for Spring-Practice-Reactive-Mongo:

```bash
kubectl create deployment spring-practice-reactive-mongo --image=spring-practice-reactive-mongo:0.0.1-SNAPSHOT --dry-run=client -o yaml > reactive-mongo-deployment.yaml
```

### Apply the Spring-Practice-Reactive-Mongo Deployment:

```bash
kubectl apply -f reactive-mongo-deployment.yaml
```

### Create a Service for Spring-Practice-Reactive-Mongo:

```bash
kubectl create service clusterip spring-practice-reactive-mongo --tcp=8080:8080 --dry-run=client -o yaml > reactive-mongo-service.yaml
```

### Apply the Spring-Practice-Reactive-Mongo Service:

```bash
kubectl apply -f reactive-mongo-service.yaml
```

Changes can be made to the [spring-practice-reactive-mongo] deployment and service configs before applying to include
environment variables as needed.

### Create Deployment for Spring-Practice-Gateway:

```bash
kubectl create deployment spring-practice-gateway --image=spring-practice-gateway:0.0.1-SNAPSHOT --dry-run=client -o yaml > gateway-deployment.yaml
```

### Apply the Spring-Practice-Gateway Deployment:

```bash
kubectl apply -f gateway-deployment.yaml
```

### Create a Service for Spring-Practice-Gateway:

```bash
kubectl create service clusterip spring-practice-gateway --tcp=8080:8080 --dry-run=client -o yaml > gateway-service.yaml
```

### Apply the Spring-Practice-Gateway Service:

```bash
kubectl apply -f gateway-service.yaml
```

Changes can be made to the [spring-practice-gateway] deployment and service configs before applying to include
environment variables as needed.

### Port Forward to access Spring-Practice-Gateway:

After deploying the Spring-Practice-Gateway, you can access it via port forwarding.
This allows you to interact with the service locally.

```bash
kubectl port-forward service/spring-practice-gateway 8080:8080
```