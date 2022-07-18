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
A collection of various commands/things which i normally forget and search for.
## Setup
I am using neovim, so the init files are present in `~\.config\nvim`. The repository exist at [github](https://github.com/aloksethi/nvim). The formatter I am using `clang-format` needs python, so make sure `pynvim` exists (also in the virtual environment)
```shell
pip install pynvim
```

## Format the file
select the line or complete file in visual mode and press ctrl-k.
Have now also added the auto formatter on save, so it will format .h,c,cpp,cc files on save

## Splitting
- `vsplit` for vertical splitting, 
- `split` for horizontal splitting, 
- Move between windows via `CTRL-W w` (or `CTRL-W arrow key`, or `CTRL-W h/j/k/l` for left/up/down/right), 
- close a window via `CTRL-W c` or `:q`, 
- make the current window the only one via `CTRL-W o`,
- split a window into two via `CTRL-W s` or `CTRL-W v` for a vertical split).
- use the `:resize` command or its shortcut `:res` to change the height of the window, for example to change the height to 60 rows, use `:resize 60`.
You can also change the height in increments too, for eample, `res +3.5`
- Use `:vertical resize `to change the width of the current window, for example, to change the width to 80 columns, `:vertical resize 80`
- Use `Ctrl-w +` and `Ctrl-w -` to resize the height of the current window by a single row. 
- Use `Ctrl-w >` and `Ctrl-w <` to resize the width of the current window by a single column. 
- To resize all windows to equal dimensions based on their splits, use `Ctrl-w =`,
- To increase a window to its maximum height, use `Ctrl-w _`,
- To increase a window to its maximum width, use `Ctrl-w |`,

Information collected from following pages, 
- [cscope tutorial](http://cscope.sourceforge.net/cscope_vim_tutorial.html)
- [vim wiki](https://vim.fandom.com/wiki/Resize_splits_more_quickly)

## Sourcing init.vim
`:source $MYVIMRC` or `:so $MYVIMRC`.
`$MYVIMRC` is a special variable present in both vim and nvim.
Check [page](https://dev.to/reobin/reload-init-vim-without-restarting-neovim-1h82) for more details.

## scriptname
`:scriptname` will show the list of files loaded

## variables
`:let` will show all varaibles.`:echo <var name>` will show the specific
variable. it will give error if the variable is not loaded.

## settings
`:set setting?` will show the value of that particular setting for example `:set foldmethod?` will tell the current fold method in use.

## folds
`zf` for creating a fold in manual mode. check foldmethod if it gives error `:set foldmethod?`. `za`, `zc`, `zd`, `zo`