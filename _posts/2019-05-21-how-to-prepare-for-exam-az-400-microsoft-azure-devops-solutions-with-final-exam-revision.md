---
layout: post
title: "How to Prepare For Exam AZ-400 Microsoft Azure DevOps Solutions With Final Exam Revision"
date: 2019-05-21 11:44:45 +0100
---

# AZ-400 Microsoft Azure DevOps Solutions Study Guide and Preparation

This post and videos will help you to prepare for **Azure DevOps Exam or AZ-400 Microsoft Azure DevOps Solutions** Exam. It gives a deep dive as well as quick revision for each area and summarizes the main learning points for a quick recap before the exam. The studying material consists of a bunch of videos and learning points that require a long time to be covered. This makes the final revision a bit challenging, which is what I tried to provide in this post. This post will not cover all learning points, but it can only provide a final and quick revision for the studying areas and points before the exam. Also, it helps to summarize some of the learning points for a quick recap at any point in time when you want to quickly remember what you have learned.

| AZ-400 Study Areas                      | Weights |
|-----------------------------------------|---------|
| Implement DevOps Development Processes  | 20-25%  |
| Implement Continuous Integration        | 10-15%  |
| Implement Continuous Delivery           | 10-15%  |
| Implement Dependency Management         | 5-10%   |
| Implement Application Infrastructure    | 15-20%  |
| Implement Continuous Feedback           | 10-15%  |
| Design a DevOps Strategy                | 20-25%  |

---

### Exam Tip: Kubernetes cluster for beginners

For more information about how to work with Kubernetes clusters and deploy them to **Azure Kubernetes Service (AKS)** and work with **Azure Container Registry**, see **[Kubernetes cluster for beginners](https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/)**

---

## Implementing DevOps Development Processes

[Implementing DevOps Development Processes](https://openedx.microsoft.com/courses/course-v1:Microsoft+AZ-400.1+2019_T1/about)

### Source Control
- Use VSTS CLI to work with Azure DevOps
  - Working with VSTS CLI enables you to automate everything as you can script anything and hook it in a build pipeline.
    - `az devops`
    - `az devops configure`
    - `az devops configure --defaults`
    - `az devops project create`
    - `az devops work item show --id 2222`
  - Migrating code
    - TFVC to Git
      - Using the web portal by clicking import repository (180 days history & less complex)
      - Using git-tfs command line tool (more than 180 and complex)
        - `git tfs clone http://tfs:8080/tfs/DefaultCollection $/Project1`
    - Git to Git
      - Using the web portal by clicking import repository
      - Using git mirror
  - Git
    - Commit
    - Branch
    - HEAD
    - Merge Non Fast-Forward (Non FF)
    - Rebase or Fast-Forward Merge (FF)
    - Squash
    - Clone
    - Remote
  - Git Branch and Merge Strategy
    - Gitflow
    - Release flow
  - Use Git Large File Storage (LFS)

### Implement & Manage Build Infrastructure
- A job is a series of tasks that run sequentially on the same target.
- In a build pipeline, the most common target is an agent. The other kind of target is the Azure Pipelines server (TFS).
- In a Release or deployment pipeline, the target can be either an **agent**, a **deployment group**, or **server** (AzDo server or TFS).
- On Linux and Windows agents, jobs may be run on the host or in a container. (On macOS and Red Hat Enterprise Linux 6, container jobs are not available.)
- Deployment targets
  - We can deploy code to multiple targets. Targets include container registries, virtual machines, Azure services, or any on-premises or cloud target that will host the application being developed, such as Microsoft Azure, Google Cloud, or Amazon cloud services.
- Remember project agent pool vs. organization agent pool and the different security permissions for each role for them like (Reader, Administrator, etc.)

### Security
- Checkmarx - A Static Application Security Testing (SAST) tool (VSTS extension)
- Whitesource for Open source library vulnerabilities and licenses (VSTS extension)
- Black Duck for Open source library vulnerabilities and licenses (VSTS extension)
- BinSkim - A binary static analysis tool that provides security and correctness results for Windows portable executables
- OWASP ZAP for penetration testing (passive tests with CI and active tests with nightly build) (VSTS extension)
- OWASP ZAP can be installed on any machine in the network, but it's better to use the OWASP Zap/Weekly docker container within Azure Container Services. This allows for the latest updates to the image and also allows being able to spin up multiple instances of the image so several applications within an enterprise can be scanned at the same time.
- Azure DevOps Security Kit (AzSk), it's a group of PowerShell cmdlets and guidance for security best practices, it scans your Azure resources (run PowerShell command) and provides a CSV file with the scan result and recommendations as fix scripts. So, you can run the recommendation fix with command as you don't need to do them manually, it's part of the cmdlets commands.
  - Infrastructure Vulnerabilities to ensure any public endpoints and ports have been whitelisted with Azure DevOps Security Kit (AzSk) (VSTS extension) we scan template and user group as part of the CI/CD
  - Microsoft Security Development Lifecycle (Threat Modeling). Use it as early as possible (shift left).
  - Using Azure Key Vault from Azure pipeline library for managing secrets
  - Azure policy, natively create policies, e.g., you create a policy from Azure (portal/CLI/REST API) to prevent the creation of VM with high cost or specific region
  - Azure Blueprints (Policies, RBAC, ARM), it's a container or a very high layer not only above the Resource Group but it can be above the Subscription to help EA (Enterprise Architect to use native Azure for their EA across the organization in a repeatable configuration manner)
  - Using Azure Blueprints & Azure Policy for governance and compliance

### Service hooks
- It's like a callback to hook Azure DevOps or make Azure DevOps call third-party actions or functions when events occur in Azure DevOps.

### App Center
- One of the important uses of App Center is to distribute mobile apps pre-release or beta releases to distribution groups (private store) like QA, Canary users, etc.
- Distribution group and its type (public/private/shared)
- Enable getting feedback from users on the new features
- Collecting crash and analysis reports

### Exam Tip: Security in DevOps
For more information about **Security practices in DevOps** and working with **Continuous Assurance**, see **[Securing Your Application, Infrastructure, Environment Continuously Using DevSecOps](https://youtu.be/VUi1LlAIRyc)**

---

## Implement Continuous Integration

[Implement Continuous Integration](https://openedx.microsoft.com/courses/course-v1:Microsoft+AZ-400.2+2019_T1/about)

### Overview
- **Variable** to store values used in the pipeline
- **Variable groups** to store values that are available across multiple pipelines.
- Predefined build variables
- Microsoft-hosted agent. Maintenance and upgrades are taken care of for us. Each time we run a pipeline, we get a fresh virtual machine. The virtual machine is discarded after one use. Like self-hosted agents, Microsoft-hosted agents can run jobs directly on a **VM** or in a **container**.
- Hosted agent for Ubuntu 16.04 doesn’t run in a container but it has Docker tool if we need to run container jobs.
- Hosted agent for Hosted macOS, data stored in the US, and managed by a third party.
- Configuring Agent Demands from build options to check for build capabilities.
- We can install a tool or runtime on the fly (even on Microsoft-hosted agents) using **Build tool installers**.

### Trigger
- CI
- Batch changes
  - If we have a lot of team members uploading changes often and to reduce the number of builds so when the build is running, the system waits until the build is completed, then queues another build of all changes that have not yet been built.
- Scheduled

### Code Quality
- SonarCloud
  - VSTS task Preparing analysis on SonarCloud
    - Connect to SonarCloud endpoint and generate a token
  - VSTS task Run Code Analysis
  - VSTS task SonarCloud build breaker (fail build when quality gates failed)

### Security
- CVE - Common Vulnerabilities and Exposures. The National Cybersecurity FFRDC, operated by the Mitre Corporation, maintains the system and releases CVEs.
  - Open source library
    - Security
    - Quality
    - Old version
    - License
- OWASP (Open Web Application Security Project)
  - The most famous document they produced is **Top 10**
  - **Top 5** from the **Top 10**
    - Injection
      - Never trust any user input
    - Broken authentication
      - Use custom or own authentication system rather than well-known authentication systems
    - Sensitive data exposure
    - XML external entities
    - Broken access control
      - Roles and permission poorly implemented or not implemented at all
  - One of the most effective steps that an organization could take towards a stronger, more secure software development culture would be to adapt the OWASP Top 10 as part of the development guidance principle.

### Container
- Dockerfile
  - Docker can build images automatically by reading the instructions from a Dockerfile. A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image. Using docker build users can create an automated build that executes several command-line instructions in succession.
  - **FROM ubuntu**
    - The first statement in the Dockerfile. It refers to the parent image that this new image will be based upon.
    - An image that doesn’t have a parent is called a base image and **FROM scratch** can be used instead.
- Docker Build
  - The **docker build** command builds an image from a Dockerfile.
- Multiple Stage Builds
  - Docker 17.05 added a new feature that allowed the creation of multi-stage builds. This helps with being able to optimize the files, improves their readability, and makes them easier to maintain.
  - With multi-stage builds, we use multiple FROM statements in our Dockerfile. Each FROM instruction starts a new stage. The stages are numbered in order, starting with stage 0. To make the file easier to maintain without needing to constantly change numbers that reference, each stage has been named (or aliased) by using an AS clause.

### Docker compose
- **Docker compose** is a tool to define and run multi-container docker applications. We configure all our containers in a single **YAML** file, then spin up all of them with a single command.
  - e.g., Let’s say that our application depends on a database, a queue, a cache, and an API service. We can define all of those dependencies as services in a docker-compose.yml file and start everything with a single command. This makes it very easy.
- Visual Studio Docker support
  - Right-click on the project --> Add --> Docker support
  - This will add Dockerfile as multiple stage build

---

### Exam Tip: Azure Pipelines Agent
For more information about how to work Azure Pipeline, see **[Deeply Understanding of Azure Pipelines Agent](https://youtu.be/IJ1IfKyvxHM)**

---

## Implement Continuous Delivery

[Implement Continuous Delivery](https://openedx.microsoft.com/courses/course-v1:Microsoft+AZ-400.3+2019_T1/about)

### Design a Release Strategy
- Releases and Deployments
  - Separating your functional release from your technical release (deployment)
- Stages
  - Customer adoption rings (for example, early adopter ring, frequent adopter ring, late adopter ring) - You typically want to deploy new or beta releases to your early adopters more often than to other users. Therefore, you are likely to have different releases in each of these rings.
  - Staging and production slots of a website - We must model the deployment to both the staging and production slots as a single stage.
  - Multiple geographic sites with the same application - We must model this as a single stage with parallel deployment to multiple sites (typically by using jobs).
- Release gates and triggers (Quality Gate, Automatic Approval based on signals collected from external services e.g. Twitter, Azure policy, etc.)
  - It’s an automated check that approves the continuation
  - Many triggers- like, Query work items result count, Invoke Azure Function, and others.
  - Evaluation option is to reevaluate the release condition every **X** minutes/hours during **Y** minutes/hours
  - No new blocker issues
  - Code coverage on new code greater than 80%
  - No license violations
  - No vulnerabilities in dependencies
  - No new technical debt introduced
  - Compliance checks
  - Are there work items linked to the release?
  - Is the release started by someone else as the code committer?
  - Is the performance not affected after a new release?
  - Pull Request triggers enable you to create pull request releases that deploy your PR code or PR builds to detect deployment issues before the code changes are merged.
  - Pre and post-deployment approval
  - Pre and post-deployment condition (release gates)
  - Release gates VSTS extension e.g. Twitter
- Track your release process quality
  - Visualizations about the quality of all the releases pipeline, e.g., adding a dashboard widget which shows the status of every release.
- Release Notes, functional and technical documentation
  - Generate Release Notes Build Task (VSTS)
  - WIKI Updater Tasks (VSTS)
  - Manuals or documentation that we release together with the product, should be treated as source code. When the product changes and new functionality is added, the documentation needs to change as well. We can store the documentation as part of your code repository or create a new repository containing the documentation. In any case, the documentation should be treated the same way as source code. Create a documentation artifact in the build pipeline, and deliver this artifact to the release pipeline. The release pipeline can then deploy the documentation to a site or just include it in the boxed product.
- Deployment Tasks
  - The choice of deployment tasks depends on the target environment to which we want to deploy our software.
  - If we want to deploy a mobile app, we can create a package and upload it with a script or use a task that directly deploys to the Apple Store or Google Play store.
  - If we want to deploy to a server running on-premises, then we might want to use a PowerShell or command line script to install the software. Or, if we are going to use a specialized task, we can use the web deployment task that deploys MS deploy packages directly on an IIS.
  - We can also use an SSH Task and use Shell tasks to execute the necessary actions on the target server.
  - When we want to deploy to Azure or another cloud, we can use command-line tools specialized for that cloud or some specialized tasks that we can use to install our resources.
  - When we want to deploy to a container cluster, we can run a docker command in a command-line task, or we can use specific docker tasks. They do a lot of the plumbing and secure connections to the container cluster and container registry.
- Jobs and Jobs Type
  - Jobs
  - Container jobs
  - Server jobs
  - Deployment group jobs
  - Multiple jobs
  - Service containers
- Multi-configuration build and deployment
  - Multi-configuration builds - e.g. build app for both **debug** and **release** configurations on both **x86** and **x64** platforms.
  - Multi-configuration deployments- e.g. for different geographic regions.
  - Multi-configuration testing - to run a set of tests in parallel - once for each test configuration.
- Service connection
  - Apple App Store
  - Docker Registry
  - ARM
- Task group
  - Group of tasks to be reused in different stages or environments in the release pipeline.
- Deployment group
  - Is a logical set of deployment target machines that have agents installed on each one. Deployment groups represent the physical environments; e.g., "Dev", "Test", "UAT", and "Production". In effect, a deployment group is just another grouping of agents that can be used by the release pipeline for executing tasks or jobs that we want to execute on our environment. This instead of executing tasks remotely from a build agent.
- Deployment queue settings
  - If we generate builds more quickly than they can be deployed, we may configure multiple agents, for example, by creating releases from the same release pipeline for deployment of different artifacts.
- Variable groups
  - To store values that are available across multiple pipelines.
  - I can add variables manually to my variable groups or I can add them from Azure Key Vault.
- Running Availability Tests (There are two types of availability tests)
  - URL ping test: a simple test that you can create in the Azure portal. You can check a URL and check the response and status code of the response.
  - Multi-step web test. These are a number of HTTP calls that are executed in sequence.
- Controlling canary release
  - Using a combination of feature toggles, deployment slots, and traffic manager we can achieve full control over the traffic flow, and enable canary release.

---

### Exam Tip: Building CI/CD with Azure Pipeline
For more information about how to work with CI/CD, see **[Deeply Understanding of Azure Pipelines Agent](https://youtu.be/i77vEEVAfB8)**

---

## Implement Dependency Management

[Implement Dependency Management](https://openedx.microsoft.com/courses/course-v1:Microsoft+AZ-400.4+2019_T1/about)

- Azure Artifacts helps security shift left, control to use only security packages that have no security vulnerability or have no open-source license issue and track the usage of all third-party libraries. To stay in control of the dependencies that are consumed, enabling governance and security scanning for the use of packages with known vulnerabilities or exploits.
- Centralized storage for packages called:
  - Package feed.
  - Repository
  - Registry
- Primary source and Upstream source.
  - Upstream sources enable you to manage your product’s OSS dependencies in a single feed. Using upstream sources makes it easy to use your favorite OSS packages, and can also give you additional protection against outages and corrupted or compromised packages. You can also publish private dependencies in the same feed that manages your OSS dependencies.
  - The package manager (VS Nuget package manager is an example) will evaluate the primary source first and switch to the upstream source when the package is not found there. The upstream source might be one of the official public sources or a private source.
  - Public package sources can be upstream sources to private feeds.
  - The upstream source could refer to another upstream source itself, creating a chain of sources.
  - Upstream sources may download and cache the packages that were requested and not cached before. The source will include these downloaded packages and start to act as a cache for the upstream source. The private feed uses the upstream source as a proxy for the external source.
  - In VS settings, we remove the checkbox from NuGet.org as we will use it as Upstream and only check our feed to make it the primary feed.
- Packages are immutable:
  - When I publish a package to a repo with a specific version, I can’t publish the same version again. Replacing or updating an existing version of a package is not allowed, we must provide a new version.
- Feeds views
  - As the feed is immutable, so we must set the version before we push or publish a package to the feed, then testing the package but if the published package has bad quality and many developers have been used it after the publish, it’s my problem because I publish and give them a bad package.
  - To solve this problem, developers used to create 2 feeds (debug & release) and when the package is tested and approved from the debug feeds, it increments the release version and pushes to the release feed. But this caused a problem because there are 2 feeds for the same package, so there is no longer SSOT (Single Source Of Truth) and also caused a lot of confusion.
  - The main idea of views is to provide a way to have the same feed for debug and release packages.
  - By default, the published package will belong to the local view only until I promote it to **Pre-release** or **Release**.
  - By filtering the feed with Release, I can see only release packages. So, for example, I can see only **1.0.15**, **1.0.30** and all between them were promoted as pre-release as they didn’t pass the test.
  - Feeds in Azure Artifacts have three different views:
    - Release: The @Release view contains all packages that are considered official releases.
    - Prerelease: The @Prerelease view contains all packages that have a label in their version number.
    - Local: The @Local view contains all release and prerelease packages as well as the packages downloaded (cached) from upstream sources.
  - @local contains all packages published directly to the feed (e.g., by `nuget push` or `npm publish`) and all packages saved from upstream sources. If you don’t use any other views, @local should be your default view.
  - The default URI of the feed is pointing to the local view and to point to the Release or Pre-release view, I have to put that as part of the URI.
- Commands:
  - List (Restore or Install)
  - Save package from upstream
  - Push package
  - Unlist/deprecate package
  - Delete
  - Download
- Roles:
  - Reader: Can list and restore (or install) packages from the feed.
  - Collaborator: Is able to save packages from upstream sources.
  - Contributor: Can push and unlist packages in the feed.
  - Owner: has all available permissions for a package feed.

---

### Exam Tip: Run Unit Test in Docker
For more information about how to Run unit testing in Docker, see **[Running Unit Tests in Docker](https://youtu.be/p-x_F6WMOgw)**

---

## Implementing Application Infrastructure

[Implementing Application Infrastructure](https://openedx.microsoft.com/courses/course-v1:Microsoft+AZ-400.5+2019_T1/about)

- Windows PowerShell DSC
  - DSC is a management platform in PowerShell that enables you to manage your IT infrastructure with configuration as code. We configure a server as pull or push to apply configuration on nodes.
- Azure Automation DSC
  - Is a configuration management service for DSC nodes, Azure Automation uses its own built-in DSC pull server to be able to apply configurations, so I don’t need to create one like Windows PowerShell DSC. I will write Window PowerShell DSC script, compile it to MOF.

### Managing configuration drift
We can manage it in our environments by using configuration management tools such as:
  - DSC
  - Azure Policy

### Modularize ARM Templates
  - Linked template
  - Nested template

### Custom Script Extension (CSE)
  - Is an easy way to download and run scripts on Azure VMs. We can run it, either during its deployment or on an existing VM.

### Azure CLI
  - Run on Linux, macOS, or Windows
  - Accessible on the machine, for Windows, we can use cmd.exe or PowerShell, and for Linux and macOS we can use Bash.
  - Accessible via browser using Azure Cloud Shell.
  - It structures as a group, subgroup, and commands.
    - `az --help` displays all groups, subgroups, and commands, e.g., `vm` is a subgroup of `az`.
    - `az vm --help`, displays all groups, subgroups, and commands for the *vm* subgroups and so on.
    - `az vm restart --help`, display all the commands in *restart* subgroup.
    - e.g., `az vm restart -g MyResourceGroup -n MyVm`
    - Find command: `az find -q MyCommand`
  - Can run:
    - Interactively: in real time, providing input as needed.
    - Scripted: where everything is predefined then executed.

---

### Exam Tip: Building IaC with Terraform, Azure, and Azure Pipeline
For more information about how to work with IaC using Terraform and **CI/CD**, see **[Building IaC with Terraform, Azure, and Azure Pipeline](https://youtu.be/KiCZzJlS16A)**

---

### Azure PowerShell
- PowerShell provides services like Shell and Command parsing.
- Base PowerShell has 2 formats:
  - Windows PowerShell
  - PowerShell core (Cross-platform, Linux, and macOS)
- Cmdlets are shipped in modules.
- Module is a .DLL that includes the code for Cmdlet.
- We load Cmdlet by loading all its modules.
- We can get the list of the loaded modules in our PowerShell session by (`Get-Module`).
- Azure PowerShell is a PowerShell module that we add to Windows PowerShell or PowerShell core for others (Linux, macOS).
- Accessible via local install (Windows, Linux, macOS).
- Accessible via browser using Azure Cloud Shell.
- Can run:
  - Interactively: in real-time, providing input as needed.
  - Scripted: where everything is predefined then executed.

### Azure VM extensions
- Run on existing VMs, which is useful when we need to make configuration changes on an already deployed VM. We can bundle VM extensions with RM template deployments. By doing so, we can deploy and configure Azure VMs without post-deployment intervention.
- Custom Script Extension (CSE) is part of Azure VM extensions.
- Example of use CSE, to download a script from a GitHub repository onto the target VM, and then run the script to enable the IIS-WebServerRole feature and configure a basic home page (HTML).
- We can store templates or scripts on Azure Storage account and secure them with a SAS token.

### Package Management
- By using package management, it’s possible to manage all aspects of software such as installation, configuration, upgrade, and uninstall.
- apt: apt is the package manager for Debian Linux environments.
- yum: Yum is the package manager for CentOS Linux environments.
- Chocolatey: Chocolatey is the software management solution built on PowerShell for Windows operating systems.

### Azure Automation
- Azure Automation account
  - Similar to Azure Storage accounts in that they serve as a container to store automation artifacts.
- Runbook
  - Is a set of tasks that perform some automated process in Azure Automation.
- Automation Shared resources
  - 8 resources that allow being used in, or associated with a runbook e.g., **Schedule**.
- Webhooks
  - A webhook allows starting a particular runbook in Azure Automation through a single HTTPS request.
- Source control integration
  - Source control allows you to push code from Azure Automation to source control, or pull your runbooks from source control to Azure Automation.
- Update Management
  - To manage OS updates For computers running Windows and Linux, for computers deployed in Azure, or in on-premises environments or in other cloud providers.

### Azure DevTest Labs
- It’s a way to provide a controlled Dev and Test VMs for your Dev and Test teams with governance for security and cost, e.g., you can specify which VM images in the marketplace are allowed to be used.
- VSTS extension for CI/CD, it can Create a VM, Create a custom image from a VM, and Delete a VM. It is useful for quickly deploying a "golden image" for a specific test task and then deleting it when the test is finished.

---

### Exam Tip: Building IaC with Ansible, Azure, and Azure Pipeline
For more information about how to work with IaC using Ansible and **CI/CD**, see **[Building IaC with Ansible, Azure, and Azure Pipeline](https://youtu.be/Q8aWeHCrGh4)**

---

## Implementing Continuous Feedback

[Implementing Continuous Feedback](https://openedx.microsoft.com/courses/course-v1:Microsoft+AZ-400.6+2019_T1/about)

### Overview
- Continuous Experimentation mindset
- Design practices to measure end-user satisfaction.
- Design processes to capture and analyze user feedback.
- Design processes to automate application analytics.

### Recommend monitoring tools and technologies
- **Synthetic Monitoring**: Ensure that internet and intranet mobile applications and web applications are tested and operate successfully from different points of presence around the world.
- **Alert Management**: Send notifications via email, voicemail, text, mobile push notifications, and Slack messages when specific situations or events occur in development, testing, or production environments to get the right people's attention and manage their response.
- **Deployment Automation**: Use different tools to schedule and deploy complex applications and configure them in development, testing, and production environments. Discuss the best practices for these teams to collaborate effectively and efficiently and avoid potential duplication and erroneous information.
- **Analytics**: Developers need to look for patterns in log messages to identify if there is a problem in the code. Operations need to do root cause analysis across multiple log files to identify the source of the problem in complex applications and systems.

---

### Using Log Analytics

- **Using Application Insight**
- **Using Azure Monitor**

---

### Designing a DevOps Strategy

- **Greenfield Projects**
- **Brownfield Projects**
- **Selecting Groups**
  - Canaries who voluntarily test bleeding-edge features as soon as they are available.
  - Early adopters who voluntarily preview releases, considered more refined than the code that canary users are exposed to.
  - Users who consume the products, after passing through canaries and early adopters.
- **Project Metrics and KPIs**
  - **Faster Outcomes**
    - Deployment Frequency: Increasing the frequency of deployments is often a critical driver in DevOps projects.
    - Deployment Speed: As well as increasing how often deployments happen, it's important to decrease the time that they take.
    - Deployment Size: How many features, stories, and bug fixes are being deployed each time?
    - Lead Time: How long does it take from starting on a work item until it is deployed?
  - **Efficiency**
    - Server to Admin Ratio: Are the projects reducing the number of administrators required for a given number of servers?
    - Staff Member to Customers Ratio: Is it possible for fewer staff members to serve a given number of customers?
    - Application Usage: How busy is the application?
    - Application Performance: Is the application performance improving or dropping? (Based on application metrics)?
  - **Quality and Security**
    - Deployment Failure Rates: How often do deployments (and/or applications) fail?
    - Application Failure Rates: How often do application failures occur, such as configuration failures, performance timeouts, etc?
    - Mean Time to Recover: How quickly can you recover from a failure?
    - Bug Report Rates: You don't want customers finding bugs in your code. Is the amount they are finding increasing or decreasing?
    - Test Pass Rates: How well is your automated testing working?
    - Defect Escape Rate: What percentage of defects are being found in production?
    - Availability: What percentage of time is the application truly available for customers?
    - SLA Achievement: Are you meeting your service level agreements (SLAs)?
    - Mean Time to Detection: If there is a failure, how long does it take for it to be detected?
  - **Culture**
    - Employee Morale: Are employees happy with the transformation and where the organization is heading? Are they still willing to respond to further changes? (This can be very difficult to measure)
    - Retention Rates: Is the organization losing staff?
  - **Lead Time vs. Cycle Time**

---

### Extra links:

- [Microsoft Learn: Azure Artifacts](https://docs.microsoft.com/en-us/azure/devops/artifacts/concepts/views?view=azure-devops)
- [Evolve your DevOps practices](https://docs.microsoft.com/en-ca/learn/paths/evolve-your-devops-practices/)
- [Build applications with Azure DevOps](https://docs.microsoft.com/en-ca/learn/paths/build-applications-with-azure-devops/)
- [DevOps Engineer Learning Path](https://docs.microsoft.com/en-ca/learn/browse/?roles=devops-engineer)
- [DevOps Engineer Resource Learning Path](https://docs.microsoft.com/en-ca/learn/browse/?roles=devops-engineer&resource_type=learning%20path)

---

You can find more information about DevOps in the following post: [Building and Deploying Your Code with Azure Pipelines](https://mohamedradwan-devops.github.io/posts/building-and-deploying-your-code-with-azure-pipelines/)
