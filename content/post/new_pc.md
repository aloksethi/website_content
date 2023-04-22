---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Installation for new PC"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2023-04-23T02:15:34+03:00
lastmod: 2023-04-23T02:15:34+03:00
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
A collection of things that I am installing on a new PC.
Not including instructions for things like `git`, `vscode`, `python` etc.

## Drivers for the display link dock
For Ubuntu 22.04.2 LTS, seems like there is a package as the older way of installing the driver by downloading from Synaptics pages does not work. The installation fails because there is some problem in the compiling phase. Instructions copied from [Tuxedo's page](https://www.tuxedocomputers.com/en/Infos/Help-Support/Instructions/Universal-Dockingstation-Drivers-Installation.tuxedo).
```
sudo apt install displaylink
```

## Deep sleep
Sleep mode still seems to be idle instead of deep. Check instructions at [tuxedo website.](https://www.tuxedocomputers.com/en/Infos/Help-Support/Instructions/Fine-tuning-of-power-management-with-suspend-standby.tuxedo)

## git config
- Configure globally the noreply email address for the [github](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-email-preferences/setting-your-commit-email-address). 
```
git config --global user.email "aloksethi@users.noreply.github.com"
```
- add the key for ssh access to github [instructions](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).

## Website editing
```
sudo apt  install golang-go
sudo apt  install hugo

git clone https://github.com/aloksethi/website_content
hugo new content/post/new_pc.md
```
