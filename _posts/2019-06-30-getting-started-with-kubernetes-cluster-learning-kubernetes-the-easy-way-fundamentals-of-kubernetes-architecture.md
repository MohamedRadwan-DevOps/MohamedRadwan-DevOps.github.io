---
layout: post
title: "Getting Started with Kubernetes Cluster | Learning Kubernetes the Easy Way | Fundamentals of Kubernetes Architecture"
date: 2019-06-30 07:42:33 +0100
---

## Introduction

Kubernetes is rapidly turning into the new standard for sending and overseeing programming in the cloud. With all the power Kubernetes gives, be that as it may, comes a precarious expectation to absorb information. As a newcomer, attempting to parse the official documentation can be overpowering. There is a wide range of pieces that make up the framework. It tends to be difficult to tell which ones are important for your utilization case. This blog entry will give a disentangled perspective on Kubernetes, however, it will endeavor to give an abnormal state outline of the most significant segments and how they fit together.


>For more information about how to work with Kubernetes cluster and deploy it to **Azure Kubernetes Service (AKS)** and work with **Azure Container Registry**, see **[Kubernetes cluster for beginners](https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/)**.
{: .prompt-tip }
{% include embed/youtube.html id='4DUhc0MjdUc' %}


## Equipment

### Node

![Kubernetes cluster Node components, Pod, volume, containerized app](/assets/images/2019/06/Node-1024x878.jpg)

A node is the littlest unit of registering equipment in Kubernetes. It is a portrayal of a solitary machine in your cluster. In most creation frameworks, a node will probably be either a physical machine in a data center or virtual machine facilitated on cloud supplier like Google Cloud Platform. Try not to give shows a chance to restrict you, in any case; in principle, you can make a node out of nearly anything. Thinking about a machine as a "node" enables us to embed a layer of deliberation. Presently, rather than stressing over the one of a kind attributes of any individual machine, we can rather just view each machine like a lot of CPU and RAM assets that can be used. Along these lines, any machine can substitute some other machine in a Kubernetes cluster. For more info about [Kubernetes cluster docs](https://kubernetes.io/docs/concepts/).

### The Cluster

![Kubernetes Cluster includes Node, Master and node processes](/assets/images/2019/06/Cluster-1024x828.jpg)

Working with individual nodes can be valuable, it's not the Kubernetes way. All in all, you should consider the cluster an entire, rather than agonizing over the condition of individual nodes. In Kubernetes, nodes pool together their assets to frame an all the more dominant machine. When you send programs onto the cluster, it astutely handles distributing work to the individual nodes for you. If any nodes are added or removed, the cluster will move around work as necessary. It shouldn't make any difference to the program, or the developer, which individual machines are actually running the code. If this sort of hivemind-like framework helps you to remember the Borg from Star Trek, you're not the only one; "Borg" is the name for the inward Google venture Kubernetes depended on.


>For more information about how to work with **Docker** like pulling docker images, running docker images, and working with containers, see **[Docker for beginners](https://mohamedradwan-devops.github.io/posts/docker-for-beginners-step-by-step-tutorial/)**.
{: .prompt-info }
{% include embed/youtube.html id='3RJv6yVfaRE' %}


### Persistent Volumes

Projects running on your cluster aren’t guaranteed to keep running on a particular node, so information can’t be saved to any arbitrary spot in the document framework. If a program attempts to save information to a record for some other time and then moved onto another node, the document will no longer be where the program anticipates that it should be. The customary neighborhood stockpiling related to every node is treated as a store to hold programs, however, any information saved locally cannot be relied upon to persevere. To store information forever, Kubernetes utilizes Persistent Volumes. While the CPU and RAM assets of all nodes are effectively pooled and overseen by the cluster, persistent document stockpiling isn’t. Neighborhood or cloud drives can connect to the cluster as a Persistent Volume.

## Programming

### Containers

Projects running on Kubernetes are packaged as Linux compartments. Containers are a broadly accepted standard, so there are now numerous pre-fabricated pictures that can be delivered on Kubernetes. Containerization enables you to make independent Linux execution conditions. Any program and all of its conditions can be bundled up into a solitary document and after that shared on the web. Anyone can download the container and deliver it on their framework with next to no arrangement required. Making a container is possible automatically, enabling CI and CD pipelines. Numerous projects can be included in a solitary container, however, you should restrict yourself to one procedure for each container if at all conceivable. It’s smarter to have numerous little containers than one huge one. If each container has a tight core, refreshes are easier to deliver and issues are easier to analyze.

### Pods

Unlike different frameworks you may have utilized before, Kubernetes doesn’t run containers straightforwardly; instead, it wraps at least one container into a higher-level structure called a pod. Any containers in a similar pod will have similar assets and neighborhood organizations. Containers can easily communicate with different containers in the same pod as if they were on the same machine while maintaining a level of separation from others. Pods are used as the unit of replication in Kubernetes. If your application becomes too popular and a single pod instance can’t deliver the load, Kubernetes can be configured to deliver new copies of your pod to the cluster as necessary. Even when not under heavy load, it is standard to have multiple copies of a pod running at any time in a production framework to allow load balancing and failure resistance. Pods can hold numerous containers, but you should limit yourself when possible. Since pods scale up and down as a unit, all containers in a pod must scale together, to their individual needs. This leads to wasted assets and an expensive bill. To resolve this, keep pods as small as possible, typically holding a fundamental procedure and its tightly coupled assistant containers.

### Deployments

Although pods are the fundamental unit of computation in Kubernetes, they are not typically directly launched on a cluster. Pods are usually handled by one more layer of abstraction, the deployment. A deployment’s primary role is to declare how many copies of a pod should keep running at once. When the deployment is added to the cluster, it will automatically turn up the requested number of pods and then monitor them. If a pod dies, the deployment will automatically re-create it. Using a deployment, you don’t have to manage pods manually. You can just declare the ideal condition of the framework, and it will be overseen for you automatically.


>For more information about how to work with **Git** with animation. All commands will be represented in graphical animation. E.g., git branch, git merge, git rebase, git cherry-pick, and many others, see **[Mastering Git with animation](https://mohamedradwan-devops.github.io/posts/mastering-git-from-beginner-to-advanced-step-by-step-with-graphical-animation-commands/)**.
{: .prompt-info }
{% include embed/youtube.html id='ZgCCnv9LxzA' %}


### Access

Using the concepts described above, you can create a cluster of nodes and launch deployments of pods onto the cluster. There is one final issue to settle: allowing external traffic to your application. By default, Kubernetes provides isolation among pods and the outside world. If you want to communicate with a service running in a pod, you need to open up a channel for communication. There are numerous ways to add access to your cluster. The most common ways are by including either an Ingress controller or a LoadBalancer. The exact tradeoffs between these two options are out of scope for this post. You should know that access is something you need to handle before you can experiment with Kubernetes.

## Conclusion

What's described above is a simplified version of Kubernetes. Yet it should give you the basics you need to start testing. Since you understand the pieces that make up the framework, it's time to use them to deliver a genuine application.