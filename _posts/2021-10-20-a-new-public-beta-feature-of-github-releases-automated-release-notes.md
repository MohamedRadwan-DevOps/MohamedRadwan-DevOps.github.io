---
layout: post
title: "A new public beta feature of GitHub Releases: Automated Release Notes"
date:   2021-10-20 23:49:30 +0100
---

GitHub is where developers come to learn and celebrate what's new in open source, and also where maintainers share, collaborate, and celebrate their community's work. One of the most important parts of the software development life cycle is delivering your software to those who use it. Read more about releases in this [GitHub document](https://docs.github.com/en/repositories/releasing-projects-on-github/about-releases). In this post are elaborated some recent improvements that are made to GitHub Releases in a new public beta version to make it easier to create and communicate compelling, high-quality releases while encouraging collaboration and engagement from the community.

From your GitHub repository, after clicking on the Releases button, we can immediately see the new UI with all new releases. For each release, we can see the contributors' highlighted names and also all first-time contributors to the project will be recognized. All of the pull requests that are part of the release are automatically identified and a short summary is created for each of them. Also, we can see notes that were being automatically generated. This is the view with the new design Releases (shown on Image 1), which is pretty much different from the older one named Tags.

![Image 1 - New view Releases](/assets/img/2021/10/Image-1-New-view-Releases-1024x488.png)
Image 1 - New view Releases

In this example, I have a repository in which a configuration is used, release.yml (shown on Image 2), in order to do a slightly more advanced form of release notes. In this configuration file, individual categories are created with titles and labels, in order to sort the content in these categories. There is also a special label star "*" which should match anything that didn't match other labels.

![Image 2 - Configuration file release.yml](/assets/img/2021/10/Image-2-Configuration-file-release.yml_.png)
Image 2 - Configuration file release.yml

In order to draft a new release, I will go into the Releases view (shown on Image 3), choose one of the existing tags or create a new one (you can also search for your tag by typing).

![Image 3 - Auto-generate release notes](/assets/img/2021/10/Image-3-Auto-generate-release-notes-1024x459.png)
Image 3 - Auto-generate release notes

Clicking on the +Auto-generate release notes button will automatically generate a preview of our release notes. By going in the Preview tab (shown on Image 4), we can see the Title for our release, all different changes divided into categories like Breaking Changes, Bug fixes, Other changes, defined by us in the *release.yml* configuration file.

![Image 4 - Preview of the automatically generated release notes](/assets/img/2021/10/Image-4-Preview-of-the-automatically-generated-release-notes-1024x518.png)
Image 4 - Preview of the automatically generated release notes

And now only by clicking Publish release, simple as that, we got our release notes automatically generated and published. In addition, the Releases UI with its new look gives communities the chance to celebrate those who contributed to each release by displaying the profile pictures of all contributors. Anyone on GitHub.com can react to releases with emoji or click to sponsor a project they wish to support.

There are two ways to automatically trigger the release notes, the workflow that we mentioned above by triggering it directly in the UI, or to cut the release locally and push the tag upstream.

One more great feature if you are automating releases with GitHub Actions, is that there is an API that you can use in your workflows to integrate the new Automated Release Notes feature right into your existing actions pipeline. A *post* request should be sent (*`/repos/${{ github.repository }}/releases'*) which will create a release. Check more details in the [API docs](https://docs.github.com/en/rest/reference/repos#create-a-release).

Using the API will give you more flexibility to select the target commit and new tag name, give the previous tag name in case you want to generate release notes that go over more than one release. You can also pass a custom configuration. Check also the [official post](https://github.blog/2021-10-04-beta-github-releases-improving-release-experience/) for this new feature on the official GitHub blog and their [official document](https://docs.github.com/en/repositories/releasing-projects-on-github/automatically-generated-release-notes) where you can find everything about Automatically generated release notes. 

Also if you want to check your changelog into your release itself, using this you will be able to generate those notes before creating the release and having that information as part of the release itself.

The most awesome thing about the new updates to GitHub Releases is that you can start using it now on all repositories on GitHub.com, it is already available and turned on by default. Check out also this post about [how to use GitHub Actions in Visual Studio only with right-click and Publish](https://mohamedradwan-devops.github.io/2021/10/06/using-github-actions-in-visual-studio-only-with-right-click-and-publish/).
