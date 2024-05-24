## Kubernetes demo from TechWorld with Nana's crash course

### K8s manifest files 
* mongo-config.yaml
* mongo-secret.yaml
* mongo.yaml
* webapp.yaml

### K8s commands

#### Start Minikube and check status
    minikube start --vm-driver=docker 
    minikube status

#### Deploy components
Configure first external configurations because they need to exist before the application starts running:
    
    kubectl apply -f mongo-config.yaml
    kubectl apply -f mongo-secret.yaml
    
Next we create database because the web app depends on it:
    
    kubectl apply -f mongo.yaml 

And to deploy the web application:
    
    kubectl apply -f webapp.yaml

#### Interacting with K8s cluster
Checking all components created in the cluster:
    
    kubectl get all

Checking config and secret maps:
    
    kubectl get configmap
    kubectl get secret

For more detailed info about a component:
    
    kubectl describe <name of component> <instance of the component>

And to check the logs to troubleshoot or debug (stream mode):
    
    kubectl logs <name of the pod> -f

#### Accessing the application
Get the minikube IP:
    
    minikube ip

Acess in browser: 
    
    <minikube IP>:<Service defined port>

#### Stop Minikube cluster
    minikube stop