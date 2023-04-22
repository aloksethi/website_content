---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "Random"
subtitle: "A collection of random bits of commands"
summary: ""
authors: []
tags: []
categories: []
date: 2022-07-19T00:52:14+03:00
lastmod: 2022-07-19T00:52:14+03:00
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
A collection of random  commands which I rarely use, but it is good to have a quick reference of.

## packages related 
Finding which package provides a particular file `dpkg -S command`

## nao QT related
basically how to make the robot_settings run on the linux box
```
export QT_DEBUG_PLUGINS=1
export QT_QPA_PLATFORM=xcb
```
this will give indication which library is missing
```
annot load library /home/asethi/Desktop/robot-settings-2.8.6.23-linux64/plugins/platforms/libqxcb.so: (/home/asethi/Desktop/robot-settings-2.8.6.23-linux64/bin/../lib/libz.so.1: version `ZLIB_1.2.9' not found (required by /lib/x86_64-linux-gnu/libpng16.so.16))
QLibraryPrivate::loadPlugin failed on "/home/asethi/Desktop/robot-settings-2.8.6.23-linux64/plugins/platforms/libqxcb.so" : "Cannot load library /home/asethi/Desktop/robot-settings-2.8.6.23-linux64/plugins/platforms/libqxcb.so: (/home/asethi/Desktop/robot-settings-2.8.6.23-linux64/bin/../lib/libz.so.1: version `ZLIB_1.2.9' not found (required by /lib/x86_64-linux-gnu/libpng16.so.16))"
```
