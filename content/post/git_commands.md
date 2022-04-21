---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Git Info"
subtitle: ""
summary: ""
authors: []
tags: [git]
categories: []
date: 2021-01-28T14:48:56+02:00
lastmod: 2021-01-28T14:48:56+02:00
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
A small collection of information regarding git

## Making a remote repo on the server

* Made a bare copy of the local repo. ` git clone --bare mlab_code git_repo.git`. `mlab_code` is the name of my local folder in which I did `git init`.
* Copied the `git_repo.git` to the remote server via scp. `scp -r git_repo.git USER_NAME@SERVER_NAME:/research/rftrx/library/`.
* Went to the remote server where the empty repo was copied and initialize it again using the shared option. `git init --bare --shared`.
* At the local machine, added the remote repository as a remote ` git remote add cwc_server ssh://USER_NAME@SERVER_NAME:/research/rftrx/library/git_repo.git`.
* Now can push to the remote `git push cwc_server master`. Syntax of git push is `git push <remote> <local_branch>:<remote_branch>`.In order to set the defaults for ths push command, execute the `git push -u cwc_server master`.

## saving password
* When on linux/WSL </br>
`git config --local credential.helper 'cache --timeout=3600000'`

## Useful links<br> 
* [Git on a server](https://git-scm.com/book/en/v2/Git-on-the-Server-Getting-Git-on-a-Server#_getting_git_on_a_server)
* [Supported git protocols](https://git-scm.com/book/en/v2/Git-on-the-Server-The-Protocols)
* [Git remote](https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes)
* [Undoing/Fixing/Removing commits from Git](http://sethrobertson.github.io/GitFixUm/fixup.html)

