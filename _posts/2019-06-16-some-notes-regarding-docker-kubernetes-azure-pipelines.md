---
layout: post
title: "Some notes regarding Docker, Kubernetes Azure Pipelines"
date: 2019-06-16 13:48:23 +0100
---

## Docker Compose

**What is Docker Compose?** Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YML file to configure your application's services. Then, with a single command, you create and start all the services from your configuration.

- In the docker-compose.yml file, we will list all services (Web API, Frontend, DB, etc).
- Check the validity of the yml file by running `docker-compose config` (path or space if inside the path where the file is).
- Fix any issues in the docker-compose.yml file.
- Run all services (containers) by running `docker-compose up -d`.
- Stop all services (containers) by running `docker-compose down`.

### Install Docker Compose

```sh
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose
```

---
layout: post
title: "Some notes regarding Docker, Kubernetes Azure Pipelines"
date: 2019-06-16 13:48:23 +0100
---

![Install Docker Compose on Linux](/assets/img/2019/06/Install-Docker-Compose-on-Linux-1024x589.png)

More info about **docker compose**: <https://docs.docker.com/compose/overview/>

### How to build docker-compose.yml

<https://docs.microsoft.com/en-us/dotnet/standard/microservices-architecture/multi-container-microservice-net-applications/multi-container-applications-docker-compose>
<https://docs.docker.com/compose/compose-file/>


>For more information about how to work with **Docker** like pulling docker images, running docker images, and working with containers, see **[Docker for beginners](https://mohamedradwan-devops.github.io/posts/docker-for-beginners-step-by-step-tutorial/)**.
{: .prompt-tip }

### Docker multi-stage build and docker builder pattern

**Docker builder pattern** involves two Docker images with two Dockerfiles. One for each image:

1. **"build"** image with all the build tools installed, capable of creating production-ready application files. E.g., an image with InstallShield to create the package.
2. **"service"** image capable of running the application. E.g., no need to have InstallShield as it's not needed to run the application.

**Docker multi-stage build** Multi-stage builds are a new feature requiring Docker 17.05 or higher. It helps to optimize Dockerfiles while keeping them easy to read and maintain. You can have multiple **FROM** statements in the same Dockerfile, allowing implementation of the builder pattern without maintaining many Dockerfiles. 

We define each stage using **AS StageName** in the FROM statement. E.g.,

- `FROM myImageName AS build`
- `FROM myImageName AS test`

You can also use a stage as your base image instead of using an image, e.g.,

- `FROM myImageName AS build`
- `FROM build AS test`

So, you create the stage for a purpose, such as building the application, unit testing the application, and then copying your application or test result (artifacts) to a mounted volume. You can then copy the artifact from the mounted volume to another stage if needed, which could be the final stage to create the image for deployment to production. The main idea is that you have a stage image that you don't need to store; you just need it on the fly to produce some files. Once you produce the files, you will take them, and that's it. You only create and store images needed for deployment to an environment.

## Docker create

The `docker create` command creates a writable container layer over the specified image and prepares it for running the specified command. The container ID is then printed to `STDOUT`. This is similar to `docker run -d` except the container is never started. You can then use the `docker start <container_id>` command to start the container at any point. This is useful when you want to set up a container configuration ahead of time so that it is ready to start when you need it. The initial status of the new container is `created`. 

More info about docker **multi-stage build and docker create**:
<https://docs.docker.com/develop/develop-images/multistage-build/>
<https://docs.docker.com/engine/reference/commandline/create/>
<https://stackoverflow.com/questions/46705781/extract-unit-test-results-from-multi-stage-docker-build-net-core-2-0>

>For more information about how to work with Kubernetes clusters and deploy them to **Azure Kubernetes Service (AKS)** and work with **Azure Container Registry**, see **[Kubernetes cluster for beginners](https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/)**.
{: .prompt-tip }

### COPY vs. ADD in a Docker file

Both COPY and ADD are Dockerfile commands that serve similar purposes: copying files from a specific location into a Docker image. COPY takes in a src and destination. It only lets you copy a local file or directory from your host (the machine building the Docker image) into the Docker image itself. ADD lets you do that too, but it also supports two other sources. First, you can use a URL instead of a local file/directory. Secondly, you can extract a tar file from the source directly into the destination.

### Copy Files Over SSH task (Azure Pipeline)

Use this task in a build or release pipeline to copy files from a source folder to a target folder on a remote machine over SSH.
<https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/deploy/copy-files-over-ssh?view=azure-devops>

### SSH task (Azure Pipeline)

Use this task in a build or release pipeline to run shell commands or a script on a remote machine using SSH. This task enables you to connect to a remote machine using SSH and run commands or a script.
<https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/deploy/ssh?view=azure-devops>

### Shell task (Azure Pipelines)

Use this task in a build or release pipeline to run a shell script using bash.
<https://docs.microsoft.com/en-us/azure/devops/pipelines/tasks/utility/shell-script?view=azure-devops>

![Azure Pipelines Shell Script task to echo AGENT_BUILDDIRECTORY](/assets/img/2019/06/Azure-Pipelines-Shell-Script-task-to-echo-AGENT_BUILDDIRECTORY-1024x790.png)

Links: Bash and PowerShell reference
<https://web1.cs.wright.edu/~pmateti/Courses/233/Labs/Scripting/bashVsPowerShellTable.html>
