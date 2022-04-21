---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Adding plotter in Virtuoso"
subtitle: "Instructions to add an EPS printer to Cadence Virtuoso"
summary: ""
authors: []
tags: [Virtuoso]
categories: []
date: 2020-01-24T00:34:47+02:00
lastmod: 2020-01-24T00:34:47+02:00
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
This is useful for printing schematics and layouts as an EPS file so that it can be send for review or printed using the available printer. In my particular case, Cadence is running on a Linux server, to which there is no printer available, so I have to somehow print to a file, which can then be converted to pdf.

## Adding the EPS plotter

Create a file named .cdsplotinit in your working directory, and add an EPS printer based on this example: 
```
p1|Encapsulated PostScript: \
        :manufacturer=Adobe: \
        :type=epsf: \
        :resolution#300: \
        :maximumPages#1: \
        :paperSize="8x8 inches" 2400 2400: \
        :paperSize="Unlimited" 72000 72000:
```		
After restarting the Cadence, there should be a printer name "p1" available.

This text is taken from now kaput link http://collaborate.bu.edu/moin/Cadence/PrintToImage (checked on 3rd Feb 2020).