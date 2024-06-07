---
layout: post
title: "The steps to run Static Application Security Testing (SAST) using Azure Pipeline"
date:   2022-12-02 15:07:23 +0100
---

We are going to use Azure DevOps Demo Generator to generate a project to
run Static Application Security Testing (SAST) to get detailed
information on security vulnerabilities and suggested fixes for quick
remediation.

1. Navigate to [DevOps Demo Generator](https://azuredevopsdemogenerator.azurewebsites.net/) to select the WhiteSource Bolt template.


<figure class="wp-block-image size-large">
<img
src="/assets/images/2023/03/Slide2-1024x576.jpg"
class="wp-image-10685" />
</figure>

You can navigate to the created project repos and choose the Readme file
to read more about the project.

<figure class="wp-block-image size-large">
<img
src="/assets/images/2023/03/Slide6-1024x576.jpg"
class="wp-image-10686" />
</figure>

2. Navigate to pipelines to edit it
3. Choose the agent we need to use Ubuntu latest or any of ubuntu
agents.
4. Select NPM Install.
5. Make sure it has the install command so it could set up the NPM.

<figure class="wp-block-image size-large">
<img
src="/assets/images/2023/03/Slide12-1024x576.jpg"
class="wp-image-10687" />
</figure>

6. Select Maven
7. Make sure to assign the pom.xml destination
8. Select WhiteSource and leave it to the default values but basically,
you should select the Repo/App you want to scan

<figure class="wp-block-image size-large">
<img
src="/assets/images/2023/03/Slide14-1024x576.jpg"
class="wp-image-10688" />
</figure>

9. Click Save & queue
10. Navigate to the pipelines after the build is done and select the
WhihteSource CI
11. Select MendBolt
This is the risk vulnerability and it has 3 types High-Medium-Low and we
have HIGH which means our application is not secure at all
Select Security Vulnerabilities
Here you can find the fix you should be doing to avoid this
vulnerability risk

<figure class="wp-block-image size-large">
<img
src="/assets/images/2023/03/Slide20-1024x576.jpg"
class="wp-image-10689" />
</figure>

<figure class="wp-block-image size-large">
<img
src="/assets/images/2023/03/Slide21-1024x576.jpg"
class="wp-image-10690" />
</figure>

Also, you can check License risks.

<figure class="wp-block-image size-large">
<img
src="/assets/images/2023/03/Slide22-1024x576.jpg"
class="wp-image-10691" />
</figure>

