---
layout: post
title: "GitHub Enterprise Server 3.1"
date:   2021-12-04 22:22:19 +0100
---

In this post we are going to see some of the new features coming to GitHub Enterprise Server 3.1. GitHub Enterprise Server 3.1 is now available to download as a release candidate. This release follows the most popular GitHub Enterprise Server release in years. GitHub Enterprise Server 3.0 brought GitHub Actions, GitHub Packages, and GitHub Advanced Security to companies self-hosting GitHub for the first time. Since then, as a response to customers' feedback, there has been an improvement in stability and ease of use across the platform. With GitHub Enterprise Server 3.1, all of those changes are incorporated alongside a host of new features - from Actions to pull requests - to help teams take ideas from code to production in less time.

This release includes:

- GitHub Actions workflow visualizations: track and troubleshoot complex workflows at a glance
- Auto-merge pull requests: automatically merge a pull request the moment it's ready
- Repository performance optimization: for large, busy repositories

### GitHub Actions: Workflow visualizations

With workflow visualizations, we can view and understand complex workflows, track the progress of workflows in near real-time, troubleshoot runs quickly by easily accessing logs and job metadata, and monitor progress deployment jobs and easily access deployment targets. GitHub Actions will now create a simple, visual graph of every workflow.

### Auto-merge pull requests: automatically merge a pull request the moment it's ready

Let's say that we have a project that is built for Android, iOS, and web, and each of those platforms has its own test suite. If the tests are successful then we have a release step as well. We have already started a pull request. Here we can use autocomplete, which works for numbered lists and unnumbered lists as well. Next, instead of having to wait for tests to run, or for the review to come back, we can go to the bottom of the pull request and enable the option auto-merge, shown on Image 1.

![Image 1 - Enable auto-merge](/assets/img/2021/12/Image-1-Enable-auto-merge-1024x590.png)
Image 1 - Enable auto-merge

Next, we can create our commit message and hit Confirm auto-merge, shown on image 2. After this, the pull request will be automatically merged when all the tests are passed and when all the required reviews have been submitted.

![Image 2 - Confirm auto-merge](/assets/img/2021/12/Image-2-Confirm-auto-merge-1024x345.png)
Image 2 - Confirm auto-merge

The next improvement that we are going to mention in this post is custom notifications. Before, in the notifications settings, we could only watch the participating option, all activity, and ignore. Now we can see one more option displayed last in the list, it is the option Custom. When choosing this option, we can choose to receive notifications for issues, pull requests, releases, or all three (shown on Image 3).

![Image 3 - Custom notifications](/assets/img/2021/12/Image-3-Custom-notifications.png)

Image 3 - Custom notifications

## Repository performance optimization: for large, busy repositories

In this release, repository performance for large mono repos has been optimized. Git right operations are now performed up to 30 times faster. When we push to a repository, a checksum is computed in order to ensure repositories remain in sync. During repair operations, sometimes those checksums are computed from scratch and sometimes it can take up to 30 seconds for large amounts of repos. Starting with 3.1 GitHub Enterprise Server now computes these replica checksums prior to taking the lock to be always under one second, allowing more write operations to succeed immediately.

## New Security features

Secret scanning is a lightning-fast engine that detects credentials in our code when they are pushed to GitHub. This feature now will be available for all GitHub advanced security customers. It scans for credentials using a broad set of patterns, including those from over 35 different partners. Additionally, repository admins on enterprise servers will now be notified immediately whenever a secret is committed to their code.

In addition to Secret scanning, there is also Code scanning. The CodeQL engine can now detect more sources of untrusted user data with new or improved support for 20 libraries and frameworks across C++, Java, Python, JavaScript.

There are also two new features in enterprise server 3.2 and beyond. The first one is the long-awaited dark mode for developers who prefer to code at night or just prefer the deeper contrast for when they work. The second feature is to verify domains, which will allow enterprise server admins to restrict what domains email notifications can go to, so they can make sure that their code stays even more secure within their enterprise.

To learn more about GitHub Enterprise Server 3.1, read the [GitHub Enterprise Server 3.1 release notes](https://docs.github.com/en/enterprise-server@3.1/admin/release-notes#3.1.0.rc1) and [download](https://enterprise.github.com/releases/3.1.0/download) it now. Check also other GitHub features in this post [A new public beta feature of GitHub Releases: Automated Release Notes](https://mohamedradwan-devops.github.io/?p=10316).
