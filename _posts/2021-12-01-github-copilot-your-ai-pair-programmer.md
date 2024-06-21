---
layout: post
title: "GitHub Copilot: your AI pair programmer"
date:   2021-12-01 00:41:05 +0100
---

In this post we are going to check the new VS code extension called GitHub Copilot. With GitHub Copilot, we can get suggestions for whole lines or entire functions right inside our editor. To sum this up, we can convert our comments into code.

The focus in this example, in order to see how the GitHub Copilot works, is starring repositories. First, we should import the Octokit and set up an Octokit instance, but before that, we are going to write a comment about that. So our comment will be:

> // The Octokit API Instance

After the comment, the following code should be added:

> const octokit = new Octokit () {

> }

After which in the editor will appear a suggestion of how to set up our Octokit instance (to set up our token).

Now we want to star a repo with the given owner and repo, but first, we should add a comment, something like the following:

> // star a repo with the given owner and repo

After pressing Tab in order to finish the comment, there should be an option to use a synchronous function in order to be able to pass this in, shown in Image 1.

![Image 1 - starRepo](/assets/img/2021/12/Image-1-starRepo-1024x591.png)
Image 1 - starRepo

After this, we can star the repo simply by typing:

> starRepo(`octokit', `rest.js');

where the owner and the repository will be already suggested.

In the next example, there is already set up a library which we are going to use, called tweet-api-client. The comment which we are going to type is:

> //Search for Tweets containing a certain phrase

> //and like them using twitter-api-client

By hitting a Tab we can actually hover over the suggested comment and we can go from next to previous comments and see all the different suggestions in order to set up this function. First we need to set up a twitter client which we are going to do by choosing the following suggestion:

> const client = new TwitterClient();

After this, we want to leverage the twitter client to start our repo. In order to do this, we are going to hit control + Enter, which is going to open up a couple of synthesized suggestions for how to get this done, shown on Image 2.

![Image 2 - Suggestions](/assets/img/2021/12/Image-2-Suggestions-1024x557.png)
Image 2 - Suggestions

We are going to use the solution shown on the image above since it has a phrase variable, we can also limit the count to 5 and we can also run the tweets. Before we run this, we are going to update several more things. The endpoint .search will be updated with tweets.search. And also what gets returned from tweets in the response is going to be updated into tweets.statuses.

Something to keep in mind, this code is generated and it is not always the utmost updated in the code. The model of copilot itself is getting trained every day, so the more people use it, the copilot will learn more suggestions and will be updated. Similar to octokit, also here we will need to pass a token. Shown on the Image 3 below, there are all tokens that we will need to interact with the twitter API.

![Image 3 - Tokens](/assets/img/2021/12/Image-3-Tokens-300x121.png)
Image 3 - Tokens

The last thing that we should do, before running this, is to update the search phrase into `#GitHubCopilot`.

After running this, we should be able to search for #GitHubCopilot, find the last five tweets and like all of them. If we check our twitter profile, we will see that the last tweets with the hashtag #GitHubCopilot are already liked.

This was only one example, but if you want to get your hand on this, definitely go to [copilot.github.com](https://github.com/features/copilot/signup) and sign up for the wait list. Trained on billions of lines of public code, GitHub Copilot puts the knowledge you need at your fingertips, saving you time and helping you stay focused. GitHub Copilot is available as an extension for Neovim, JetBrains, and Visual Studio Code. It might be interesting to check also [Using GitHub Actions in Visual Studio only with right-click and Publish](https://mohamedradwan-devops.github.io/2021/10/06/using-github-actions-in-visual-studio-only-with-right-click-and-publish/).

GitHub Copilot works with a broad set of frameworks and languages. The technical preview does especially well for Python, JavaScript, TypeScript, Ruby, Java, and Go, but it understands dozens of languages and can help you find your way around almost anything. Skip the docs and stop searching for examples. GitHub Copilot helps you stay focused right in your editor.
