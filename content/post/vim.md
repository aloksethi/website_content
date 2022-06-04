---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "nvim"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2022-06-04T23:35:54+03:00
lastmod: 2022-06-04T23:35:54+03:00
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

# Setup
I am using neovim, so the init files are present in `~\.config\nvim`. The repository exist at [github](https://github.com/aloksethi/nvim). The formatter I am using `clang-format` needs python, so make sure `pynvim` exists (also in the virtual environment)
```shell
pip install pynvim
```

# Format the file
select the line or complete file in visual mode and press ctrl-k.

# Splitting
`vsplit` for vertical splitting. `split` for horizontal splitting.