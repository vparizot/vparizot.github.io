---
permalink: /halloweenAnimatronics/
title: "Embedded Systems and MicroPs in Halloween Animatrons"
author: "Victoria Parizot"
# date: "10/31/2024"
# categories:
#   - reflection
# draft: false
---

Around this time of year, Halloween decorations are unavoidable. If you have ever gone trick-or-treating or gone to a Spirit Halloween, you might have been startled by one of those scary animatron. 

This Halloween, I've engaged with these decorations differently -- and admire the embedded systems that allow these guys to run. To understand these systems better, I have looked at some dissassembly videos, and see that most of these systems have a relatively simple core and intricate housings. For example, motors, LED lights, and sound modules connect to a central controller to produce a jarring effect. 

Now that I have some experience designing embedded systems, I can imagine how I can use my electronics tool box to create my own animatron. For my blog I opted to do a brainstorming exercise of how I would design a halloween animatron with the MCU and FPGA. 

One animatron I saw this season was of a witch that would stir a cauldron and laugh when motion was detected. 

{% include figure popup=true image_path="/assets/images/misc/witch.jpeg" caption="An animatron kind of like this" %}

<!-- ![An animatron kind of like this](images/witch.jpeg)  -->

This design would require a motion sensor, motor, speaker, and controller. If I were to design this, I would treat the motion sensor as a trigger that would envoke a series of motor and speaker operations. I would use an FSM to wait until motion was detected by waiting for an voltage input connected to a motion sensor like [this one](https://mm.digikey.com/Volume0/opasdata/d220001/medias/docus/695/EKMC160711x_Spec.pdf 
) was high. 

I think my FSM would look something like this:

{% include figure popup=true image_path="/assets/images/misc/witchFSM.jpeg" caption="FSM for Halloween Animatron" %}

<!-- ![FSM for Halloween Animatron](images/witchFSM.jpeg)  -->


What I am amazed by is the simplicity of a system that can be so effective, going to show that usually not the difficulty of a project that makes a project effective, but the idea. 

## Sources: 
Here are the youtube videos of the dissassemblies that I watched.

https://www.youtube.com/watch?v=b-kKYJtPMec
https://www.youtube.com/watch?v=t6dM9zDjjXo
https://www.youtube.com/watch?v=ccejC5heTpA