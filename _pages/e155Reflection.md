---
permalink: /e155Reflection/
title: "Reflection: Debugging & Presentation"
description: "A Reflection on E155 MicroProcessors"
author: "Victoria Parizot"
# date: "12/13/2024"
# categories:
#   - reflection
draft: false
---

## Intro
With E155 coming to a close, I would like to reflect on the class, especially the final project. In all my time at Mudd, I had never learned so much from nor given so much to a class. The first half of the class, we developed our debugging skills as we completed labs that familairized us with the FPGA and MCU. The last month, the class split into pairs to complete a final project of their choosing. My partner, Audrey, and I decided to make a DJ Deck. 


## DAC Troubles
Perhaps the biggest technical stuggle of the lab was the disaster of outputting audio. We were able to read in audio into the FPGA two weeks into the project, using a PCM1808 ADC with I2S communication. However, we didn't get audio playing until two days before final checkoffs. 

We had originally planned to used I2S to communicate between the FPGA and MCU. However, the MCU did not have a I2S peripheral, only an configurable Serial Audio Interface (SAI). Despite reading the reference manual countless times, we still had trouble aligning the needed Bit clock, Left/Right clock, Frame size, and Slot size. Moreover, online forums were discouraging the onboard DAC for outputting audio due to it's low resolution. As a result, we decided to pivot to an external I2S DAC that could output directly from the FPGA. When we got the external DAC, we wired it according the the datasheet directly to the PCM1808 ADC with the FPGA acting as the clock controller. However, we were not getting an output from the DAC. Using the logic analyzer, we confirmed that the clock rates were as desired and that the ADC was outputting audio. We also confirmed the configuration with a multimeter against online tutorials. Despite being confident in our set up, the DAC was not outputting any signals. 

At this point, we were running out of time. We decided to pivot back to using the MCU DAC, and opted to use SPI to comunicate the audio data. We already had one-way SPI communication to input filter values. Also, I had already configured DMA and the DAC on the MCU, such that once we read in the variable it would output. 

After a few all nighters, some second perspective from fellow students in the lab, and a LOT of debugging, we were finally able to send and output audio onto a speaker, only with a little problem -- The audio sounded TERRIBLE. When looking at our output on the oscilliscope, the bottom half of the waves were inverted. After some thinking, and Prof Brake's, help we realized that this was a type casting issue. The ADC reading in the audio would output digital audio centered at zero, meaning that we were trying to output negative values on the DAC. As the DAC could only output positive voltages, it would assume two's complement. 

After fixing this bug, we still had an issue -- We were only able to output frequencies below 400 Hz, or else we would get aliasing. My first thought was that timing was off. But, we were inputting and outputting audio at 44 kHz, which was the minimum frequency needed to capture the full range of human hearing by Nyquist's Theorem. This caused us to look at the timing withing the system -- before landing on the SPI clock. We were sending samples too slowly, causing some samples to be lost. To fix this problem, we maximized the SPI clock, to ensure that the entire system can keep up with the 44 kHz sampling rate. We even went farther, and increased our sampling rate to 98 kHz.

At this point, we were hearing exactly what we wanted to from our speakers -- and nothing could bring me and Audrey down. I was so happy, that as we commented our code and worked on our final report, I would listen to my playlists through the deck -- and it sounded as good as if I were plugged into my own computer.

## Presentation is Key
At this point, Audrey and I wanted to go all out on Demo Day. I made a nice box in the wood shop to encapsulate our system, and we decided to bring a few props to Demo Day to truely provide the DJ vibes. We brought sunglasses, my disco ball, a spot light, and a smoke machine -- all to set up in the DIGITAL lab (At this point, you might see the problem that neither sleep deprived Audrey nor I saw). We set everything up and plugged in the smoke machine, in the DIGITAL lab. The second that smoke machine went off, Audrey and my face dropped, realizing instantly how incredibly dumb our idea had been. Audrey rushed to shove something to stop the smoke and unplug the machine and I started to whip my sweater around to clear the smoke out of the room. Of course, Professor Harris had to walk in at this exact moment, giving a sympathetic and curious look. Audrey and I got UNBELIEVABLY lucky that the smoke detectors did not go off. 

When we told Professor Brake about our almost million-dollar mistake during Demo Day, his response was, "this happened to me when I was in undergrad." A very calm, characteristic response from Professor Brake. I think if Audrey and I had a few more hours of sleep between us, we would have saw the bad idea before the machine started going off.

## Shout Out Friends & Community

Overall, I am happy about the outcome of this project. I learned a lot about debugging, spend A LOT of quality time with Audrey, and we had a working DJ deck at the end of it. I feel much more comfortable tackling embedded systems on my own, and got well aquainted with reading datasheets and reference manuals. This semester was full of curveballs, both from MicroPs and life, but I'm happy with the ability of my peers and I to finish the semester strong. 

Huge thank you to my fellow MicroP-ers --especially Audrey, Troy, Max, Luke, and Alisha-- for their willingness to offer a second eye. Another huge thanks to Kavi, who would offer valuable advice and remind us why we wanted to do this project. Thank you to Claire and Lucie for being willing to leave a day later for Thanksgiving break. Finally, thank you to Professor Brake, Xavier, and Jacob for their help debugging!

