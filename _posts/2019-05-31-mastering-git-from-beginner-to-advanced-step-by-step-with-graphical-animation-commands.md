---
layout: post
title: "Mastering Git From Beginner to Advanced Step by Step With Graphical Animation Commands"
date: 2019-05-31 14:48:14 +0100
---

Git for Beginner and Advanced with Step by Step using Graphical Animation Commands. - [Git Tutorial](https://www.youtube.com/watch?v=ZgCCnv9LxzA) - This git tutorial video will help you learn Git with animation. It will help you deeply understand [Git](https://git-scm.com/) commands from the ground up. It will explain commands in graphical representation with animation which will make it very easy to understand different Git commands. You will understand and see how the Git tree is structured and how it\'s working, how to branch and merge, and what is the difference between merge (non fast-forward) and rebase (fast-forward merge). You will also learn how to use [cherry-pick](https://git-scm.com/docs/git-cherry-pick), how to squash before the merge, moving HEAD, and many others. Content will be covered in this video:

- Animated git branch
- Animated git merge
- Animated git cherry-pick
- Animated git rebase


>For more information about how to work with Kubernetes clusters and deploy them to Azure Kubernetes Service (AKS) and work with Azure Container Registry, see [Kubernetes cluster for beginner](https://mohamedradwan-devops.github.io/posts/getting-started-with-kubernetes-cluster-ci-cd-for-azure-kubernetes-service/)
{: .prompt-info }

[Git Tutorial - Part 2](https://www.youtube.com/watch?v=4DUhc0MjdUc)

Some points that will be covered in the video: It will be a walkthrough of git commands as step-by-step with graphical animation for git tutorial. This will be for beginners and advanced users too. I will talk about some of the git basics commands and explain how each command works. This will be through animation. I\'m not going to talk about git configuration or git architecture or git components but instead, I will focus only on git commands but with animation. At the end, this video should help you to understand what is Git? How to work with Git? What are the basic commands of Git? and many other questions.

The first part of this git training will show a demo of git commands in a graphic with animation, for example, how to create a branch, git rebase the fast-forward (FF), git merge or non-fast-forward (non FF). We will also see how to cherry-pick some of the changes instead of merging all the changes in the branch and many others. Then we will go for a demo with a command-line where we can apply what we have learned in the animation and map this command-line to the animation. This will help you understand more about these commands and represent them in your mind.

### Git Commit

What is git commit? A commit is the delta that has only the new changes. This is why each commit points to the parent commit or which commit it is based on. Because git is optimized for resource utilization, it only has the delta with each commit. To get, for example, a snapshot with all the changes, it means that you need to get all the changes starting from this commit back to all the commits.

>For more information about DevOps, what is DevOps, how to work with DevOps, what is Continuous Integration, and what is Continuous Delivery. What is the difference between CI pipelines and CD pipelines and many other topics? See [DevOps for beginners](https://mohamedradwan-devops.github.io/posts/devops-tutorial-for-beginners-developing-ci-cd-pipelines-continuous-integration-and-deployment/)
{: .prompt-info }

[DevOps Tutorial](https://www.youtube.com/watch?v=SrYCkrlpwzs)

### Git Branch

What is the git branch? A Git branch isolates new commits starting from this point, which will keep pointing to the parent commit before the isolation. Once you create a branch it means that you would like to have more commits in an isolated way.

### Git Merge (Non-Fast-Forward)

What is git merge non-fast-forward? Git merge is a new special commit that has two parent commits. Think of it as creating a new commit that points to two parents, one being the original parent (the last commit from the parent branch) and the last commit from the current branch.

### Git Rebase (Fast-Forward)

What is git rebase fast-forward? Git rebase re-applies the new commits. Instead of having two parent commits, it will copy and recreate the new commits on the target branch from the commit that starts the isolation. The last commit or the merge commit will only have one parent.

### Git HEAD

The git HEAD points to where your new commit will go. Let\'s say, I made some changes and usually the changes are either adding new files, editing an existing file, or deleting an existing file. We will call them changes. After making some changes, I start to commit them. I will type git commit and we will see that I will have a new comment which has only the delta of my changes. We will see that the master branch points to the commit as well as the HEAD.

### Git Branch Creation

Now let\'s say that I want to have a new branch to isolate new commits in it. I will start by creating a new branch with `git branch new-branch-name`. Once I have created the branch, the HEAD will point to the same commit which is still pointed to by the master branch. If I commit now, let\'s say I make some changes and then do a git commit, this will not commit to my new branch. Instead, it will commit to the master branch because I didn\'t move the HEAD to the new branch. Yes, I created the branch but the HEAD was still pointing to the master branch, not the new branch. To have my changes and new commits go to a branch, I need to move the HEAD first to that branch by `git checkout branch-name`.

### Git Reset

I can move the HEAD by using `git reset --hard commit-id`. We can also move the HEAD or detach it using refs.

### Git Cherry-Pick

We can use cherry-pick to pick only some changes without including other changes or commits.

### Start Working with Git

To start working with Git, open your directory where you want to start working and type `git init` which will initialize git. This will create git files. To see these files, we just need to open the hidden files to see them. These git files are responsible for tracking the changes and history. Then start making changes, commit the changes. Also, you can add git remote to push your changes to a remote repo on the cloud.

The video will explain all that command and more with animation.

DevOps is very important for software development and delivery. You can find more information about DevOps in the following post: [Building and Deploying Your Code with Azure Pipelines](https://mohamedradwan-devops.github.io/posts/building-and-deploying-your-code-with-azure-pipelines/)
