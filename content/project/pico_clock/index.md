---
# Documentation: https://wowchemy.com/docs/managing-content/

title: " 7-segment clock"
summary: ""
authors: []
tags: [RP2040]
categories: []
date: 2023-04-30T00:42:17+03:00

# Optional external URL for project (replaces project detail page).
external_link: ""

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Custom links (optional).
#   Uncomment and edit lines below to show custom links.
links:
 - name: Git Repo	
   url: https://github.com/aloksethi/elephant_clock
   icon_pack: fab
   icon: github


url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: ""
---
## History
Had promised Sumi long time ago that I will fix her elephant poop clock. Further, agreed to convert it to a digital clock instead of an analog one. In aticipation of fixing 7segment display even made hole in the original clock face but never managed to actually build a clock.

## PCB design
Intial version of the pcb can be found from github. This version does not contain any smarts.

## Software
```
sudo openocd -f interface/jlink.cfg -c "transport select swd" -c "adapter speed 500" -f target/rp2040.cfg -c "program pwm_led_fade.elf verify reset exit
```
