---
title: Blog with Gatsbyjs
date: "2018-02-18T17:48:00.000Z"
layout: post
draft: false
path: "/posts/blog-with-gatsbyjs/"
category: "frontend"
tags:
  - "frontend"
  - "gatsbyjs"
  - "react"
description: "Gatsbyjs is a new static site generator. It features reactjs, graphql and many more 
modern frontend best practices. It's a perfect framework for creating blogs. This article is to summarize how
this blog is created within this framework."
---

This blog is focused on parts not introduced in Gatsbyjs official tutorial. For Gatsbyjs, the official doc is very informative.

## Choose the Starter
Gatsbyjs has a few official starters and 3rd party starters. These starters serve the purpose of 
scafolding and quick start. I chose this one called [lumen](https://github.com/alxshelepenok/gatsby-starter-lumen).

## Using the Starter to start
Run `gatsby new project-name https://github.com/alxshelepenok/gatsby-starter-lumen`.
This creates an folder called project-name locally. You should create an github repo called project-name in github.
Also set up git in your project with `git init`. Then tell Gatsby where to deploy your site by adding the git remote address with https or ssh. Here is how to do it with https: `git remote add origin git@github.com:username/project-name.git`.

## Make it deployable to Github Pages
First add gh-pages as a devDependency of your site by running `npm install gh-pages --save-dev`.
Secondly create an CNAME file containing your customized domain name.
Then create an npm script to deploy your project by adding following into `package.json`. 
```
"deploy": "gatsby build && cp ./CNAME public/ && gh-pages -d public"
```

Now run npm run deploy. Preview changes in your GitHub page `https://username.github.io/project-name/`. You can also find the link to your site on GitHub under Settings > GitHub Pages.

## Configure your DNS
If you are using customized domain name, you need to point your domain name to the github page. You need to create
an CNAME entry with name as WWW and value is your github page domain (ex: jingzhouluo.github.io). Note this should be the root of your github page.

To configure the apex domain (The ones without www), you need to create two A type entry with @ as name `192.30.252.153` and `192.30.252.154` as value.

## Deploy
After running `npm run deploy`, you will notice there are two branches created. Do not manually change the gh-pages branch, always update the master branch and run the deploy command. That gh-pages branch will be updated automatically. It is served as the release branch.

