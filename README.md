# Webserver on Kubernetes

This project intend to be an example of a webserver running on Kubernetes, or simply K8s. To achieve that was used tools like Go, kind, and Docker.

## Files and folders

```sh
webserver_on_k8s
    │   Dockerfile
    │   go.mod
    │   main.go
    │   README.md
    │   webserver.exe
    │
    └───k8s
            pod.yaml
            replicaset.yaml
            service.yaml
```

## Commands used

### Creating cluster

Asking Kind to create a k8s cluster

```bash
$ kind create cluster --name=<name-of-cluster>
```

Example:
```bash
$ kubectl get nodesNAME                     STATUS   ROLES           AGE   VERSION
aula-k8s-control-plane   Ready    control-plane   9d    v1.24.0
```

### Creating docker image

After create you Dockerfile you have to build the image

```bash
$ docker build -t joseamat/webserver .
```

To push your image to the Docker Hub use this command:

```bash
$ docker push joseamat/webserver:<tagname>
```

The image needs to be in a container registry. In this case we are using the Docker Hub

### Applying yaml's 

```bash
$ kubectl apply -f k8s/<filename>.yaml
```