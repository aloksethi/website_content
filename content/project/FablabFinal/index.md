---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "ALWL"
summary: "The project I made for the Fabacademy 2019"
authors: []
tags: [Fablab]
categories: []
date: 2019-07-14T00:32:47+03:00

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
 - name: Project
   url: http://fabacademy.org/2019/labs/oulu/students/alok-sethi/projects/final-project/
   icon_pack: fas
   icon: graduation-cap

 - name: Fablab home page
   url: http://fabacademy.org/2019/labs/oulu/students/alok-sethi/
   icon_pack: fas
   icon: graduation-cap

 - name: Git Repo	
   url: https://github.com/aloksethi/alwl/
   icon_pack: fab
   icon: github

#url_code: "https://github.com/aloksethi/alwl/"
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
[//]: # ( As I am still working on the project, I will list all the updates to it on this page.)

## History
This project took a lot of different turns. It started as a desk lamp with features like wake up alarm clock, mood lighting etc,. Besides the software, all the hardware was ready by the end of Fabacademy. After the Fabacademy, I decided to also add wireless connectivity and some sort of time keeping via a RTC clock. For that purpose, I chose a bluetooth module (HC-05), a RTC(AT24C32) and decided to use ATmega328P instead of the ATmega16u2. Thus, I ordered the components from popular Chinese website and started making a PCB with ATmega328P. By the time it took for the components to arrive, I had already lost any interest to work on the software again and had started to play with other things instead. Furthermore, I later realized that the bluetooth module will not work with my phone and while fixing the OLED display to the front panel, I managed to break it. It seems that I will never finish this project in its original desired form.

Fast forward to January of 2020, I decided to install a warm white LED strip in my room. I chose SK6812 strip. I decided to use the ATmega328P controller board and a IR remote for control. One version of that is complete and installed and this page is for the details of the same.

## Parts
* SK6812 strip
* Old Laptop charger brick
* ATmega328P
* IR Remote (https://osoyoo.com/wp-content/uploads/2017/04/IMG_1772.jpg)
* IR detector (TL1838)(https://osoyoo.com/wp-content/uploads/2017/04/4-1.jpg)
* Buck converter (https://www.tme.eu/fi/en/details/oky3502-2/converter-modules/okystar/)

The IR remote and detector were part of Keysight DIY Car Kit, which was just re-branded Osoyoo DIY car kit (https://osoyoo.com/2017/08/06/osoyoo-robot-car-diy-introduction/)

## Details

### Hardware
#### ATmega328P board

Finally, have a PCB with the ATmega328P. Gerber can be downladed from the Github. The designed board is a four layer board.
Unfortunately, I associated a wrong footprint with the programming header so cannot plug the programming cable from the Atmel ICE directly. 
Below are the images of how the header is actually placed and how it was supposed to be placed.


{{< figure  library="true" src="header_pcb_layout.JPG" title="Programming header in the layout"  numbered="true" lightbox-group="header" >}}
{{< figure  library="true" src="header_pcb_schm.JPG" title="Programming header in the schematic" numbered="true" lightbox-group="header" >}}

### Software

