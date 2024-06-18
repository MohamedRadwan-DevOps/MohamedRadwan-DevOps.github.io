---
layout: post
title: "Front-end Code Quality (JavaScript Unit Test and Linting) Automation With VSTS Build"
date: 2018-04-04 06:25:31 +0100
---

## Introduction 

Frontend development became vital now for many applications development. Like SPA (Single Page Application), Mobile development and Dynamics 365 as well. So keeping and increasing the code quality is very important. I have created some videos which walk you through how to improve the code quality of the frontend development as the following.

>If you would like to know more about Azure deployments, have a look at the post [How to deploy to Azure using Team Services Release Management](https://mohamedradwan-devops.github.io/posts/how-to-deploy-to-azure-using-team-services-release-management/). The post describes how Azure deployments are made easy by using Visual Studio Team Services (VSTS) Release Management. You will see a step-by-step tutorial on how to configure and deploy to Azure in Release Management, and, moreover, how to configure an end-to-end pipeline for deploying applications on Azure.
{: .prompt-tip }

## Frontend Code Quality Introduction and abstract

Introduction and overview of a series of videos about enhancing Frontend development code quality, it includes understanding different types of JavaScript unit testing frameworks like [**Jasmine**](https://jasmine.github.io/), Mocha, Jest, different types of task runner like Grunt and [**Gulp**](https://gulpjs.com), different types of linting tools, like [**JSHint**](http://jshint.com/), ESLint, JSLint, CSSLint, different types of code formatter like Prettier and Tidy, how to write your first JavaScript using test with Jasmine standalone version, How to run JavaScript unit tests using Grunt, Command Line and [**PhantomJS**](http://phantomjs.org/), how to calculate code coverage for JavaScript unit tests using [**Istanbul**](https://istanbul.js.org/), how to run JavaScript unit tests using Visual Studio Test Explorer using chutzpah extension, how to linting JavaScript code using JSHint and how to run that from Command Line using [**Grunt**](https://gruntjs.com), finally it shows how to integrate all the quality practices with [**Visual Studio Team Service**](https://www.visualstudio.com/team-services/) Build automation so it can be part of CI/CD or Continuous Integration and Continuous Delivery.

{% include embed/youtube.html id='sOptXMvePqE' %}

## 1- Writing your first JavaScript unit test using Jasmine standalone version 

How to write your first JavaScript unit test using Jasmine as a BDD or Behavior Driven Development framework. How to use Jasmine standalone version and reference the code under test, to change the configuration in specrunner.html file, you will see also how to use beforeEach to inject the needed elements of the DOM of the HTML and how to remove them using afterEach after running the tests. This video is a prerequisite for all the coming videos if you don’t know Jasmine.

{% include embed/youtube.html id='f6f46eRxBCg' %}

## 2- Running Jasmine JavaScript unit test from command line using Grunt

How to run JavaScript Unit test written in Jasmine from Command Line using Grunt and PhantomJS. It includes how to install Node.js with NPM (Node Package Manager), how to install Grunt CLI (Command Line Interface), how to install contrib-jasmine npm, and how to create Node.js default configuration file (packages.json), to creating the first Gruntfile.js configuration file, to setting the configuration to run Jasmine inside Gruntfile.js. Finally, how to ignore node_modules from Git source control so it will be ready for build automation in further videos.

{% include embed/youtube.html id='qk91C1WbPRA' %}

## 3- Running Jasmine JavaScript unit test from Visual Studio Command Line Runner and Grunt 

How to run JavaScript Unit test written in Jasmine from Visual Studio by using Command Task Runner extension which provides a command line embedded inside Visual Studio. This extension supports different task runners as well as PowerShell and others. We will see how to install the extension, how it reads and understands Gruntfile.js and finally how to run the JavaScript unit tests from it.

{% include embed/youtube.html id='_IvOC39cpM8' %}

## 4- Running Jasmine JavaScript unit test from Visual Studio Test Explorer using Chutzpah 

How to run JavaScript unit tests written in Jasmine using Visual Studio Test Explorer and Chutzpah extension, the main idea that this extension is a test adapter for Visual Studio so it helps Test Explorer to understand Jasmine JavaScript unit tests, it’s compatible with other JavaScript frameworks as well like Mocha and Qunit, using Chutzpah, we don’t need any Grunt or Gruntfile.js as this extension uses Jasmine standalone version behind the scenes.

{% include embed/youtube.html id='gjRM-tTZwcw' %}

>You can see this video, if you would like to find more information about how to get started with Release Management and its advantages. See how to create a build definition using CI/CD Tools for VSTS Extensions (I will be using Package Extension and Publish Artifact tasks). And also using DevOps-VSTS-POC trigger in order to enable CI, all of that in order to be able to publish, share, install, and query versions. You will see how to create a release definition, choose an artifact and configure source for the artifact and default version. See how to create different environments or clone the existing one, in my case I am going to create QA, Preproduction, and Production environment. Each with one phrase and one task. See also how to configure Publish Extension task for each environment. See an end-to-end continuous delivery pipeline using VSTS extension with Build and Release Management.
{: .prompt-info }
{% include embed/youtube.html id='uGAcWLnSU0A' %}

## 5- Running Jasmine JavaScript unit test with code coverage using Istanbul and Grunt 

How to calculate code coverage for JavaScript unit tests written in Jasmine using Istanbul. We will see how to install contrib-jasmine Istanbul, how to tweak the Gruntfile.js Jasmine task to include the code coverage settings, how to see the result of the code coverage as HTML version as well as from Command Line and Visual Studio Command Task runner too.

{% include embed/youtube.html id='Clmjd7MrgR4' %}

## 6- Running JavaScript code quality tool with JSHint and Grunt

How to scan JavaScript code for better code quality enhancements and suggestions using Static Code Analysis or Linting tools. In this video we will see how to use JSHint, how to download the grunt-contrib-jshint npm, we will see also how to change the Gruntfile.js configuration to include JSHint settings and run that from Command Line and Visual Studio Command Task Runner.

{% include embed/youtube.html id='ekFaRprcmWo' %}

## 7- Running JavaScript unit test with Jasmine, code coverage, JSHint as build automation with VSTS 

How to integrate all the code quality practices: JavaScript unit test with Jasmine, code coverage for unit tests with Istanbul, linting JavaScript code quality with JSHint, and configure Visual Studio Team Service Build automation so it can be part of CI/CD or Continuous Integration and Continuous Delivery pipeline for frontend development.

{% include embed/youtube.html id='fiNxQKIRv5Y' %}

>You can see this video, if you would like to find more information about a walkthrough introducing the Release Management and Build Automation using TFS 2017/2015. Step by step about all process, starting from creating the project, check in the code in the source control, create a build definition and trigger the build, and also create a release pipeline. Learn how to configure properly the build steps, including Copy Files and Publish Build Artifacts. See how to create new release definition, add environments and link to build definition. Afterwards see how to add tasks to the release definition, like Windows Machine File Copy and configure it properly.
{: .prompt-info }
{% include embed/youtube.html id='vev3Czaa1pA' %}
