This project intends to get familiar with k3s and k3d.

What is the difference between k3s and k3d?

k3s: Lightweight Kubernetes, built for Iot and Edge computing. Runs direclty on the host.
k3d: Lightweight wrapper, to run k3s in docker. It uses Docker to create and manage containers that act as Kubernetes nodes.

k3d and Argo cd

- Create a k3d cluster
```k3d cluster create mycluster```

- Verify the cluster
```kubectl cluster-info```

- Deploy a test pod
```kubectl create deployment nginx --image=nginx```
```kubectl get pods```

- Delete the cluster 
```k3d cluster deleter mycluster```

What is a namespace?

It is a way to divide ressources between multiple users, teams or applications. You can use namespaces to organize your working environment (e.g., dev, staging, prod) or teams.
Kubernetes comes with a few built-in namespaces:
- default
- kube-system (for Kub systemn components)
- kube-public (publicly accessible data)

- To list all namespaces
```kubectl get namespaces```

- To see details about a specific namespace
```kubectl describe namespace [my-app]```

- To ensure the ArgoCD server pod is running and healthy:

```kubectl get pods -n argocd```

```kubectl port-forward svc/argocd-server -n argocd 8080:443```


Ingress is a Kubernetes resource that manages external (or internal) HTTP and HTTPS access to services in a cluster. It provides routing rules to direct traffic to different services based on the hostname or path in the request.