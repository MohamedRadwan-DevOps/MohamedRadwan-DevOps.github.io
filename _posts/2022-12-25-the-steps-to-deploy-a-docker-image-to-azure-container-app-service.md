---
layout: post
title: "The steps to Deploy a docker image to Azure Container App Service."
date:   2022-12-25 11:30:09 +0100
---

1. Navigate to-[Azure Portal](http://portal.azure.com/) and log in.
2. Select Create a Resource.
3. Select Create on the Web App.

<figure class="wp-block-image size-large">
<img
src="/assets/img/2023/03/Slide2-1024x576.png"
class="wp-image-10696" />
</figure>

4.1 Select Create new.-
4.2 Put any desired name to name the RG.
5.1 Put any desired unique app name.
5.2 Select Docker Container.
5.3 Select Linux.
5.4 Select Change size.

<figure class="wp-block-image size-large">
<img
src="/assets/img/2023/03/Slide4-1024x576.png"
class="wp-image-10697" />
</figure>

6.1 Select Production.
6.2 Select P1V2.
6.3 Select Apply.
6.4 Select Review + create.
7. Create
8. Go to the created resource.
9. Navigate to your app URL to examine it:

<figure class="wp-block-image size-large">
<img
src="/assets/img/2023/03/Slide8-1024x576.png"
class="wp-image-10698" />
</figure>

10. You can see your App URL-is working but we still haven't deployed
the Docker image yet.
11. Navigate to-[Azure DevOps-](http://dev.azure.com/)and select
"Releases" from pipelines.
12. Select New pipeline.
13.1 Change the CD name to any desired Name.
13.2 Select Empty job.
14.1 Select Add An artifact.
15. Select docker hub.

<figure class="wp-block-image size-large">
<img
src="/assets/img/2023/03/Slide14-1024x576.png"
class="wp-image-10699" />
</figure>

16. Navigate to-[DockerHub](http://hub.docker.com/).
16.1 Select your App repo.
16.2. Add the required info (Service connection, Namespace, Repository)

<figure class="wp-block-image size-large">
<img
src="/assets/img/2023/03/Slide18-1024x576.png"
class="wp-image-10700" />
</figure>

17.1 Press on + to add a new task
17.2 Search for Azure web.
17.3 Add Azure Web App for Containers.

<figure class="wp-block-image size-large">
<img
src="/assets/img/2023/03/Slide20-1024x576.png"
class="wp-image-10701" />
</figure>

18. Select your Azure Subscription.
19. Select your app from Azure.
20. Set the Docker Image name.

<figure class="wp-block-image size-large">
<img
src="/assets/img/2023/03/Slide22-1024x576.png"
class="wp-image-10702" />
</figure>

21. Press on Create release

<figure class="wp-block-image size-large">
<img
src="/assets/img/2023/03/Slide26-1024x576.png"
class="wp-image-10703" />
</figure>

22. Navigate to the app URL and check if it's working as expected.

