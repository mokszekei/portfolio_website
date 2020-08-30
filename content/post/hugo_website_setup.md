+++
author = "Siqi Mo"
title = "Build personal website with HUGO"
date = "2020-08-25"
description = "Sample article showcasing basic Markdown syntax and formatting for HTML elements."
tags = [
    "HUGO",
    "GitHub Pages",
    "html",
    "macOS",
]
categories = [
    "GitHub Pages",
    "Hugo",
]
series = ["Themes Guide"]
aliases = ["migrate-from-jekyl"]
+++

This article offers a sample guide of setting up personal website with HUGO and publishing it with GitHub Pages in macOS.
<!--more-->

Nowadays, people are showing the great things they are building by publishing websites. Instead of making website from raw HTML and CSS, we can use Static site generators, like Jekyll, Octopress, Pelican, Middleman, and Hugo. I picked Hugo to build my blog.

# Hugo site creation

The following content refered to https://themes.gohugo.io/anatole/ and https://gohugo.io/getting-started/quick-start/ .

### Step 1: Install Hugo

For MacOS users, it’s recommended to do it through homebrew, just like for most open-source software.

```
brew install hugo
```

### Step 2: Create new site

The following will create a new Hugo site in a folder named "filenam" under root directory. Default root directory for MacOS will be /Users/yourID. All the file required to finish the website would be in this folder.

```
hugo new site filename
```

### Step 3: Construct a theme

One of the adcantages of Hugo is that it contains many nice themes, see [themes.gohugo.io](https://themes.gohugo.io). I picked [Anatole](https://themes.gohugo.io/anatole/).

Then, enter your site’s directory you just created, download the theme from GitHub to this directory.
```
cd filename
git init
git submodule add https://github.com/lxndrblz/anatole.git themes/anatole
```
Then, create site configuration:
```
echo 'theme = "anatole"' >> config.toml
```

With this code, config.toml would contain basic information for the website. Then you can edit config.toml with text editor.I would recommend [Sublime Text](https://www.sublimetext.com).

> For a beginer, I suggest copying the [demo config.toml](https://github.com/lxndrblz/anatole/blob/master/exampleSite/config.toml) of the theme. Then we can modify parameters correspondingly. Documentation of each theme would always discuss the parameters in details.

### Step 4: Post new blog

Now we would be able to add new post to our blog. For example, we can create brand-new post.

```
hugo new posts/my-first-post.md
```
For me, I downloaded the [example](https://github.com/lxndrblz/anatole/tree/master/exampleSite) content files of the them. These files gave me a quick insight of the post format. Then I would be able to modity the content e.g. adding images, paragraphs,and codeboxes.

### Step 5: Run the Hugo server 

With this code, you can see your new site at http://localhost:1313/.
```
hugo server -D
```
# Website Publication with GitHub Pages

[GitHub Pages](https://pages.github.com) provides really convenience method to publish personal website. There is no need to configure server and set up database.

### 1: Create a repository 

[Create a new repository](https://github.com/new) named username.github.io, where username must be your **username on GitHub**. Then clone the new repository in the folder you would like to store this project.
```
git clone https://github.com/username/username.github.io
```
### 2: Deploy Hugo site

GitHub Pages can not actually recognize the file format of hugo. Therefore, we would need to generate HTML files that can be read by Github for Hugo site. To do this, we firstly need to open config.toml and make the following modification:
```
baseURL = "https://mokszekei.github.io/"
languageCode = "en"
DefaultContentLanguage = "en"
title = "Website of Siqi Mo"
theme = "anatole"
summarylength = 10
enableEmoji = true
enableRobotsTXT = true
publishDir = "mokszekei.github.io"
```
Hugo will now know it need to output our HTML files to <github_username>.github.io. Go to the directory of your Hugo project, run the following command:
```
hugo
```
Then Hugo will generate the HTML which customize the content in your site. All of these html, css files would be in ```public``` folder. The next step we can do is copying and pasting files inside ```public``` to the GitHub repository. And then, post it.

```
git add .
git commit -m "host my website"
git push origin master
```
Then we are done. You shoud be able to view your website **https://username.github.io**. 



{{< figure src="/images/github.png" title="github pages" >}}
























