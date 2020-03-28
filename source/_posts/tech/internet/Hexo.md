---
layout: post
title: Setup blog with Hexo
date: 2020-3-28
categories: [tech, blog]
tags: [tech, blog]
urlname: 1
---

## Preface

I deployed personal blog on [Github Pages](https://pages.github.com/) five years ago. I used Jekyll framework since it was recommended by most of the guides at that time. And it can automatically be built by Gibhub Pages.    
But I have little experience on HTML/CSS/JavaScript, it seems hard for me to make better user experience with Jekyll. So now in 2020, I decide to try [Hexo](https://hexo.io/) which is another blog framework. 

The intention of this blog is recording the tricks/issues I encounter during the deployment with `Hexo`.

<!-- more -->

## Hands on

### Installatioin

I use ubuntu 19.10 for this deployment.

1. Node

`Hexo` is powered by `node.js`, so we need install `node` firstly.  
I tried to use `snap` to install `node` as suggested by [official guide](https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions-enterprise-linux-fedora-and-snap-packages). But I encouter the [permission issue](https://stackoverflow.com/q/48910876/7325336). I solved the problem by using `nvm` instead of `snap`.
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.2/install.sh | bash
nvm install stable
```
2. Hexo

It is pretty easy to install hexo.
```bash
npm install hexo-cli -g
```
> Use following command to setup proxy for npm if necessary
> ```bash
> npm config set https-proxy http://<host>:<port>
> ```

### Create Hexo project

TBD

### Deploy on Github Pages

TBD

## Conclusion

`Hexo` is easier for me to setup a personal site with better user experience. And it has many themes, plugins and configurable options.  
I'd like to recommend it over Jekyll J.
