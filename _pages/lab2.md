---
title: "Multiplexed 7-Segment Display"
description: "An introduction to multiplexing with seven segment displays."

permalink: /multiplexingProject/

---
*An introduction to multiplexing with seven segment displays.*
## Introduction & Learning Objectives
<!-- Brief (e.g., 3-5 sentence) description of the main goals of the assignment and what was done. -->
In this project, I implemented a time-multiplexing scheme to drive two seven-segment displays with a single set of FPGA I/O pins. These displayed two independent hexadecimal numbers read from seperate DIP switches and was driven by a single seven-segment decoder HDL module. I also displayed the sum of the numbers on five LEDs. In doing so, I practiced application of transistors and modular verilog.

More information on the lab requirements can be found on the [E155 Lab 2 Course Page](https://hmc-e155.github.io/lab/lab2/).

## Design 
<!-- Explanation of design approach. How did you go about designing and implementing the design? -->
To implement this lab, I had to consider: How should I organize this module in Verilog? How fast should I switch between displays? What transistor type should I use? How do I trigger the transistor? Should I use an anode or cathode display? What resisitor values should I use to protect the FPGA? And so on. 

To work my way through these questions, I drew a block diagram. Essentially, I pass through two 4-bit signals from the two DIP switches. I then use the on-board high-speed oscillator to act as a selector signal into a 2-to-1 mux that will select an input signal to pass through the single seven-segment decoder HDL module. I then send the decoded signal to both seven-segment cathode displays. I then utilized the selector signal to drive transistors to trigger each display when needed. By using an NPN transistor, I was able to ensure that the current draw/sink on all FPGA pins are below the currents specified in the recommended operating conditions.

<!-- ![Block Diagram](/assets/images/lab2/Lab2BlockDiagram.jpeg)  -->
{% include figure popup=true image_path="/assets/images/lab2/Lab2BlockDiagram.jpeg" alt="Block Diagram" caption="Block Diagram" %}

The source code for the project can be found in the associated [Github repository](https://github.com/vparizot/e155-lab2).

## Testing
To verify that the design would work as expected, I ran simulations on ModelSim. To do, I instantiated testbenches to test each module. In my testing, I considered edge cases and general cases to examine the behavior of each module. For example, I tested the summing LEDs to ensure that they correctly summed the values of the two DIP switches in binary when they would cause overflow.

The wave forms are below, and the behavior is as expected. 

<!-- ![Wave forms for validation testing of 2-to-1 mux](/assets/images/lab2/mux_tb_wave.png)  -->
{% include figure popup=true image_path="/assets/images/lab2/mux_tb_wave.png" alt="Wave forms for validation testing of 2-to-1 mux" caption="Wave forms for validation testing of 2-to-1 mux" %}

<!-- ![Wave forms for validation testing of summing LEDs](/assets/images/lab2/sum_tb_wave.png)  -->
{% include figure popup=true image_path="/assets/images/lab2/sum_tb_wave.png" alt="Wave forms for validation testing of summing LEDs" caption="Wave forms for validation testing of summing LEDs" %}

<!-- ![Wave forms for validation testing of seven segment module](/assets/images/lab2/SevenSegments_tb_wave.png)  -->
{% include figure popup=true image_path="/assets/images/lab2/SevenSegments_tb_wave.png" alt="Wave forms for validation testing of seven segment module" caption="Wave forms for validation testing of seven segment module" %}

## Implementation
After confirming that my design would work in simulation, it was time to wire everything up based on the following circuit schematic I drew up. In my design, I used a cathode seven segment display along with NPN transistors for each digit. 

Since the display requires substantial current, more than an FPGA output pin can drive, I used an NPN transistor to drive the large current. To calculate the resistor values, I went to the data sheet and found that FPGA pins drive at 3.3 V and 8 mA.

<!-- ![Resistor calculations for NPN transistors](/assets/images/lab2/resistorCalculations.jpeg)  -->
{% include figure popup=true image_path="/assets/images/lab2/resistorCalculations.jpeg" alt="Resistor calculations for NPN transistors" caption="Resistor calculations for NPN transistors" %}

I also implemented the necessary resistors for all led display, based on [previous calculations.](/setup/#seven-segment-logic-design)

<!-- ![Circuit Schematic](/assets/images/lab2/Lab2Schematic.jpeg)  -->
{% include figure popup=true image_path="/assets/images/lab2/Lab2Schematic.jpeg" alt="Circuit Schematic" caption="Circuit Schematic" %}

<!-- Here is a video of the completed design!
![Completed design demo!](/assets/images/lab2/multiplexDemo.mov)  -->

Through trial and error, a suitable switching speed was found so that both sides of the display look like they are on!

 
## Conclusion
<!-- Number of hours spent working on the lab are included. -->

<!-- Statement of whether the design meets all the requirements. If not, list the shortcomings.-->
This project provided an introduction to implementing multiplexing in a visual manner. As a result, I grew more familiar with the different type of transistors and calculations for current draw. 

<!-- Lab 2 meets all the requirements, and took me approximately 13 hours. -->
