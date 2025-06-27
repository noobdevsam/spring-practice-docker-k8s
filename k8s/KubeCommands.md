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
kubectl create deployment my-mongo-db --image=mongo:latest --dry-run=client -o yml -> mongo-deployment.yml
```

### Apply the MongoDB Deployment:

```bash
kubectl apply -f mongo-deployment.yml
```

### Create a Service for MongoDB:

```bash
kubectl create service clusterip my-mongo-db --tcp=27017:27017 --dry-run=client -o yml -> mongo-service.yml
```

### Apply the MongoDB Service:

```bash
kubectl apply -f mongo-service.yml
```

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
kubectl create deployment my-mysql-db --image=mysql:latest --dry-run=client -o yml -> mysql-deployment.yml
```

### Apply the MySQL Deployment:

```bash
kubectl apply -f mysql-deployment.yml
```

### Create a Service for MySQL:

```bash
kubectl create service clusterip my-mysql-db --tcp=3306:3306 --dry-run=client -o yml -> mysql-service.yml
```

### Apply the MySQL Service:

```bash
kubectl apply -f mysql-service.yml
```

### View logs for MySQL:

```bash
kubectl logs my-mysql-db-<pod-id>
```

### Delete Service and Deployment for MySQL:

```bash
kubectl delete service my-mysql-db
kubectl delete deployment my-mysql-db
```