# kubernetes_mongo
mongo express and mongo db on minikube cluster

## Instructions for running cluster

### Install docker engine (Below instructions for OS: Ubuntu 18.04 or 20.04)

### Install minikube
```
#update package indexes and download recents
sudo apt-get update -y && sudo apt-get upgrade -y

#install minikube and alias kubectl
wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 && sudo chmod 755 /usr/local/bin/minikube

#alias kubectl comes with minikube 
alias kubectl="minikube kubectl –"

#version check
Minikube version; kubectl version
```
### Clone this repository

### Switch to a user in the docker group and change ownership of directory
1. `useradd -d /home/<username> -G docker <username>`

2. `sudo -u <username> -s` 

3. `chown -R $USER:$(id -g) <repo dir> && cd <repo dir>`

### Configure and start kubernetes cluster with minikube on single node
```minikube start --driver=docker```

### Create deployments/service, secret, configmap
```kubectl apply -f $(pwd)```

### Create and assign external ip addr to external service
```minikube service <service name>```

### Now access mongo express app at the given url in command line and use admin:<pass> combination (can be found in mongo-express deployment log)
![mongo express web ui](./mongo_express_webui)

## Monitoring status of cluster

### Check events
```kubectl get events <deployment name>```

### Check logs
```kubectl get log <deployment name> –timestamps=true -f ``` 

### Deployment info
```kubectl describe pod <pod name> ```

### Cluster dashboard
```minikube dashboard```


## Pause, Stop and delete cluster

### Pause and unpause cluster
```minikube pause``` ```minikube unpause```

### Stop running cluster
```minikube stop```

### Delete cluster
```minikube delete```


#### @Gaurav-Shinde

