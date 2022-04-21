---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Web reference"
subtitle: "Quick Hugo and markdown reference"
summary: "listing the usual commands I use"
authors: []
tags: []
categories: []
date: 2020-01-24T00:35:23+02:00
lastmod: 2020-01-24T00:35:23+02:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---
# Hugo
* Creating a new post. Go to the root of the website and fire the below command. By default the title of the post will be the filename. 
```
cd personal_website\website
hugo new content\post\hugo_start.md
```
Take a note on \ or / for the path. On mingw, use
```
hugo new content/post/hugo_start.md
```
Command options from the webpage as reference https://gohugo.io/commands/hugo_new/
```
hugo new [path] [flags]
-D, --buildDrafts            include content marked as draft
```
* Starting the local webserver. Here `-D` includes the draft pages.
```
hugo -D serve
```