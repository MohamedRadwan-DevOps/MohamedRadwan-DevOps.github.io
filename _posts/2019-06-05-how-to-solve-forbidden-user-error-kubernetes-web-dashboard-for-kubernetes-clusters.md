---
layout: post
title: "How to solve forbidden user error Kuberneters web dashboard for Kuberneters clusters"
date:   2019-06-05 06:35:46 +0100
---

This post will help with Kubernetes error solving. I was trying to
access [Kubernetes](https://kubernetes.io/) web dashboard for Kubernetes clusters for
[Azure Kubernetes
Service](https://azure.microsoft.com/en-gb/services/kubernetes-service/) (AKS) using the following command.

```
az aks browse --resource-group AKSRG --name aksmohamedradwan
```

I faced the following error:

![configmaps is forbidden User system serviceaccount kube-system kubernetes-dashboard cannot list configmaps in the namespace default](/assets/img/2019/06/configmaps-is-forbidden-User-system-serviceaccount-kube-system-kubernetes-dashboard-cannot-list-configmaps-in-the-namespace-default-1024x581.png "configmaps is forbidden User system")

>For more information about how to work with Kubernetes
cluster and deploy it to **Azure Kubernetes Service (AKS)** and work
with **Azure Container Registry**, see **[Kubernetes cluster for
beginner](https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service)**
{: .prompt-tip }

{% include embed/youtube.html id='4DUhc0MjdUc' %}

**Kuberneters dashboard error**

```
configmaps is forbidden: User "system:serviceaccount:kube-system:kubernetes-dashboard" cannot list configmaps in the namespace "default"
persistentvolumeclaims is forbidden: User "system:serviceaccount:kube-system:kubernetes-dashboard" cannot list persistentvolumeclaims in the namespace "default"
secrets is forbidden: User "system:serviceaccount:kube-system:kubernetes-dashboard" cannot list secrets in the namespace "default"
services is forbidden: User "system:serviceaccount:kube-system:kubernetes-dashboard" cannot list services in the namespace "default"
ingresses.extensions is forbidden: User "system:serviceaccount:kube-system:kubernetes-dashboard" cannot list ingresses.extensions in the namespace "default"
daemonsets.apps is forbidden: User "system:serviceaccount:kube-system:kubernetes-dashboard" cannot list daemonsets.apps in the namespace "default"
pods is forbidden: User "system:serviceaccount:kube-system:kubernetes-dashboard" cannot list pods in the namespace "default"
events is forbidden: User "system:serviceaccount:kube-system:kubernetes-dashboard" cannot list events in the namespace "default"
deployments.apps is forbidden: User "system:serviceaccount:kube-system:kubernetes-dashboard" cannot list deployments.apps in the namespace "default"
replicasets.apps is forbidden: User "system:serviceaccount:kube-system:kubernetes-dashboard" cannot list replicasets.apps in the namespace "default"
jobs.batch is forbidden: User "system:serviceaccount:kube-system:kubernetes-dashboard" cannot list jobs.batch in the namespace "default"
cronjobs.batch is forbidden: User "system:serviceaccount:kube-system:kubernetes-dashboard" cannot list cronjobs.batch in the namespace "default"
replicationcontrollers is forbidden: User "system:serviceaccount:kube-system:kubernetes-dashboard" cannot list replicationcontrollers in the namespace "default"
statefulsets.apps is forbidden: User "system:serviceaccount:kube-system:kubernetes-dashboard" cannot list statefulsets.apps in the namespace "default"
```

The system service account has not enough permission. So, I needed to
add permission as the following:

```
kubectl create clusterrolebinding kubernetes-dashboard -n kube-system --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

If you want to remove the permission, you can use the following command


```
kubectl delete clusterrolebinding kubernetes-dashboard -n kube-system
```

Even after I give permission, it doesn\'t work and I had to remove
Kubectl and install again as the following:

```
az aks install-cli
```

If you have the following error: Error message: 

![Unable to connect to the server dial tcp 1 8080 connectex No connection could be made because the target machine kubentes](/assets/img/2019/06/Unable-to-connect-to-the-server-dial-tcp-1-8080-connectex-No-connection-could-be-made-because-the-target-machine-kubentes.png "Unable to connect to the server dial tcp")

You just need to
connect to AKS by run get credential using the Resource Group and Azure
Kuberneters Service (AKS) as the following

```
az aks get-credentials --resource-group AKSRG --name aksmohamedradwan
```

>For more information about how to work with **Docker** like, pull docker
image, run docker image and work with container, see **[Docker for
beginners](https://mohamedradwan-devops.github.io/posts/docker-for-beginners-step-by-step-tutorial/)**
{: .prompt-info }
{% include embed/youtube.html id='3RJv6yVfaRE' %}

Now the dashboard can be
opened 

![Access the Kubernetes web dashboard in Azure Kubernetes Service (AKS)](/assets/img/2019/06/Access-the-Kubernetes-web-dashboard-in-Azure-Kubernetes-Service-AKS-1024x509.png "Access the Kubernetes web dashboard in Azure Kubernetes Service (AKS)")

