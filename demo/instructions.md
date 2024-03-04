# Demo Instructions

**Requirements**

- [Docker Desktop](https://docs.docker.com/desktop/install/mac-install/)

**Architecture**

- Chip: Apple M2 Pro
- macOS: Sonoma `14.3.1`

### Step 0: Install and start minikube

- To install [minikube](https://minikube.sigs.k8s.io/docs/start/) I used [Homebrew](https://brew.sh).

  ```sh
  brew install minikube
  ```

- Start [minikube](https://minikube.sigs.k8s.io/docs/start/)

  ```sh
  minikube start --driver=docker
  ```

### Step 1: Deploy the pods

```sh
# external config
kubectl apply -f mongo-config.yaml
kubectl apply -f mongo-secret.yaml
# database
kubectl apply -f mongo.yaml
# web application
kubectl apply -f webapp.yaml
```

### Step 3: Check the componets

Get basic information about k8s components.

```sh
# control plane node
kubectl get node
# pods info
kubectl get pod
# services info
kubectl get svc
# both
kubectl get all
```

to extended information

```sh
kubectl get pod -o wide
kubectl get node -o wide
```

To get detailed information about a specific component

```sh
kubectl describe svc {svc-name}
kubectl describe pod {pod-name}
```

### Step 4: Access the deployed application

> :warning: **Known issue - Minikube IP not accessible**

```sh
minikube service webapp-service
```

#### Resources

- mongodb image on Docker Hub: https://hub.docker.com/_/mongo
- webapp image on Docker Hub: https://hub.docker.com/repository/docker/nanajanashia/k8s-demo-app
- k8s official documentation: https://kubernetes.io/docs/home/
- webapp code repo: https://gitlab.com/nanuchi/developing-with-docker/-/tree/feature/k8s-in-hour
