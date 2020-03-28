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
$ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.2/install.sh | bash
$ nvm install stable
```
2. Hexo
It is pretty easy to install hexo.
```bash
$ npm install hexo-cli -g
```
> Use following command to setup proxy for npm if necessary
> ```bash
> npm config set https-proxy http://<host>:<port>
> ```

### Create Hexo project
Create a project named "blog"
```bash
$ hexo init blog
$ ls -l blog/ | tr -s " " | cut -d " " -f1,6-9
total
-rw-rw-r-- Mar 28 05:08 _config.yml
drwxrwxr-x Mar 28 05:09 node_modules
-rw-rw-r-- Mar 28 05:09 package-lock.json
-rw-rw-r-- Mar 28 05:08 package.json
drwxrwxr-x Mar 28 05:08 scaffolds
drwxrwxr-x Mar 28 05:08 source
drwxrwxr-x Mar 28 05:08 themes
$ cd blog
$ npm install
```
Posts can be put in `source/_posts/` folder. And there's a `hello-world.md` sample by default.

#### Deploy on Github Pages
1. Create repo
In order to deploy the project to `Github Pages`, we need create a github repo for hosting the project. We can do this by following the [official guide](https://help.github.com/en/github/working-with-github-pages/creating-a-github-pages-site)

2. Install `hexo-deployer-git`
Then we can use [hexo-deployer-git](https://github.com/hexojs/hexo-deployer-git) to deploy the project to github.
```bash
$ npm install hexo-deployer-git --save
```

3. Configure `_config.yml` for hexo
My configuration is as below,
```bash
deploy:
  type: git
  repo: https://github.com/yuanli-cn/me.git
  branch: gh-pages
  name: yuanli-cn
```

4. Deploy
Use the following command to deploy,
```bash
$ hexo g
$ hexo d
```

### Customization
Now, the site should be online with default theme and configurations.

I'd like to customize the site a bit more.
1. Change the theme
The most popular theme is [next](https://github.com/theme-next/hexo-theme-next),  we can just clone it to the `themes` folder:
```bash
$ git clone https://github.com/theme-next/hexo-theme-next themes/next
```
Then, we can set the theme in main *Hexo root config* `_config.yml`:
```bash
theme: next
```
2. Change `next` configurations
  The configuration file `_config.yml` is under `themes/next` folder.
  - Using dark mode
  ```bash
  darkmode: true
  ```
  - Change scheme
  `next` has 4 default schemes, the most popular one is `Pisces`
  ```bash
  #scheme: Muse
  #scheme: Mist
  scheme: Pisces
  #scheme: Gemini
  ```
  - Change highlight_theme
  ```bash
  highlight_theme: solarized dark
  ```
3. Add `CNAME` for own domain
This is required by `Github Pages` if we need to access this site by our own domain URL.
The `CNAME` file should be put under `themes/next/source/` folder:
```bash
$ cat themes/next/source/CNAME
yuanlicn.xyz
```

## Conclusion
`Hexo` is easier for me to setup a personal site with better user experience. And it has many themes, plugins and configurable options. 
I'd like to recommend it over Jekyll J.
