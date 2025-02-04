---
permalink: /sevenSegments/
title: "An Exploration of the Hidden Aesthetics of Electrical Components"
description: "The Design Behind Segment Displays" 
# date: "9/5/24"
---

This week I worked through the setup of the STM32L4 and iCE40 development board. (Learn more about the project [here](/setup/). This blog is heavily inspired by [Michiel de Boer (Posy)'s video on segmented displays.](https://youtu.be/RTB5XhjbgZA?si=4bg0tpS0L5QZIPHH)

As part of this setup, I worked to make a seven segment display count in hexadecimal based on the binary value of a DIP switch. 

Throughout the week, I was impressed how seven equally sized segments arranged in two stacked squares was able to display unique digits and letters A thru F. I also saw different ways people deployed the display to represent the number and letters -- using lowercase, uppercase, centering on different sides, and so on. This led me to look more at the design of segmented displays. 

<!-- ![Lab 1 Display](images/lab1Demo.MOV)  -->

The first recorded segmented display is from a 1903 patent by Carl Kingsey as a way to improve telegraph speeds. Since then, countless different segmented displays for different purposes has emerged. 

{% include figure popup=true image_path="/assets/images/misc/carlKingsey.png" caption="Carl Kingsey's segmented display, 1903" %}

<!-- ![Carl Kingsey's segmented display, 1903](images/carlKingsey.png)  -->

Perhaps the most common display is the stacked square design, which I used in lab 1. Looking closely at the display, you can observe the compromises that had been made to simplify the representation of numbers and some letters to fit into 7 equally sized segments. However, these inaccuracies have been heavily normalized to the point where I no longer recognize them. This design has been so heavily widespread that these digit representations are interchangeable with the numbers they represent.

I ask you to look around your room and see how many segmented displays you can find. I did this exercise in my dorm room and found the segmented display used to show the volume of my speaker, settings of the AC unit, and tell the time from my watch.

{% include figure popup=true image_path="/assets/images/misc/acDisplay.jpeg" caption="AC Unit Display" %}

<!-- ![AC Unit Display](images/acDisplay.jpeg)  -->

{% include figure popup=true image_path="/assets/images/misc/speakerDisplay.jpeg" caption="Speaker Display" %}

<!-- ![Speaker Display](images/speakerDisplay.jpeg)  -->


The different implementations of the segmented display goes to show how small changes are used to improve accuracy and influence aesthetics. For example, the edges of the segments could be rounded or pointed. The middle segment is sometimes slanted. The thickness of the segments change from display to display, and sometimes the entire digit is italicized. Different changes will sacrifice complexity and the look of certain numbers in favor of the look of other numbers and letters.This can be particularly useful for displays that only need to display some of the digits.

These seemingly small changes can change the impact of the design, making them suitable for different applications. A seven segmented display on a sports watch will vary from the display of public transport or a toy. 

This has led me to look more about the design choices made in embedded systems that I interact with. The rest of this blog is dedicated to share different segmented displays that surround me. 

## Segmented Displays Around Me

{% include figure popup=true image_path="/assets/images/misc/multimeter.jpg" caption="Multimeter in the digital lab included additional asymetrical segments -- My favorite segmented display yet!" %}

<!-- ![Multimeter in the digital lab included additional asymetrical segments -- My favorite segmented display yet!](images/multimeter.jpg)  -->

{% include figure popup=true image_path="/assets/images/misc/variety.jpg" caption="A Variety of segmented displays available in the engineering stockroom." %}

<!-- ![A Variety of segmented displays available in the engineering stockroom.](images/variety.jpg)  -->

{% include figure popup=true image_path="/assets/images/misc/TempGauge.jpg" caption="The temperature gauge in the engineering building." %}

<!-- ![The temperature gauge in the engineering building.](images/TempGauge.jpg)  -->

{% include figure popup=true image_path="/assets/images/misc/microwave.jpg" caption="The microwave uses a traditional design." %}

<!-- ![The microwave uses a traditional design.](images/microwave.jpg)  -->

{% include figure popup=true image_path="/assets/images/misc/WaterFountain2.jpg" caption="The water fountain uses a matrix display." %}

<!-- ![The water fountain uses a matrix display.](images/WaterFountain2.jpg)  -->

{% include figure popup=true image_path="/assets/images/misc/WaterFountain1.jpg" caption="It seems like most water fountains use the matrix display." %}

<!-- ![It seems like most water fountains use the matrix display.](images/WaterFountain1.jpg)  -->