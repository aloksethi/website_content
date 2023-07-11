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
Intial version of the pcb can be found from [github](https://github.com/aloksethi/elephant_clock/tree/382a91634d4d7cd10169b17d9923d2881dcca411/pcb/clock). 
However, managed to make a major fuckup and put the PMOS responsible for switching the digits upside down.
Second version of the pcb can be found from [github](https://github.com/aloksethi/elephant_clock/tree/9f9269e4c4915cff903a9206dc0a136ee07d0cf9/pcb/clock).
Following are the changes in PCB comapred to v1
1. Fixed the orientation of the PMOSes.
2. Increased the footprint of the SOIC16 in order to do a better soldering job.
3. Added a diode to act as a current limiting device.
4. Added a ground ring on the back copper to help probing.
5. Added markers on copper layer to help orient while assembling.
6. Added the elephant meditating footprint on front copper.

## Assembly
- Use machine pins for the through-hole 7-segment displays. Had found one 7-segment device whose DP segment was shorted to ground. If I had soldered all the 7-segments as I did while testing v1, I would not have been able to figure out the issue.

## Debugging
- Initially used j-link as a debugger. But somehow the debug pins of the PICO died after couple of days. My guess is I used VTarget as 5V instead of 3.3V and that fried the debug pins after some time. Now, I am using the pico-probe to debug the code. [forum post](https://forums.raspberrypi.com/viewtopic.php?p=2106456#p2106456).
- Even with a hardware debouncer for switches, had noticed that multiple interrupts occur for every single button press. Might be related to slow rising-falling voltages on the gpio pin which might be messing the PICO. Seems like, I do have to use a software debouncer. There is no Schmitt trigger based buffer before the  signal goes to the PICO gpio. However, my understnding was that there is already a schmitt trigger inside the PICO, so no additional one is required.[RPI forum post](https://forums.raspberrypi.com/viewtopic.php?p=2112183#p2112183).

## Software

Openocd command for using j-link.
```
sudo openocd -f interface/jlink.cfg -c "transport select swd" -c "adapter speed 500" -f target/rp2040.cfg -c "program pwm_led_fade.elf verify reset exit
```
Openocd command for using pico-probe as debug adapter.
```
sudo openocd -f interface/cmsis-dap.cfg -c "adapter speed 5000" -f target/rp2040.cfg -s tcl
```
