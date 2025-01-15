---
permalink: /setup/
title: "Lab 1: FPGA and MCU Setup and Testing"
description: "An exploration and set up of the MCU and FPGA development boards through assembly, programming, simulation, debugging, and hardware implementation." 

# author: "Victoria Parizot"
# date: "9/4/24"
# categories:
#   - reflection
#   - labreport
# draft: false

---
## Introduction & Learning Objectives
<!-- Brief (e.g., 3-5 sentence) description of the main goals of the assignment and what was done. -->
In this lab, I familiarized myself with the [STM32L432KC](https://hmc-e155.github.io/assets/doc/ds11451-stm32l432kc.pdf) microcontroller unit (MCU) and [UPduino v3.1](https://hmc-e155.github.io/assets/doc/FPGA-DS-02008-2-0-iCE40-UltraPlus-Family-Data-Sheet.pdf) field-programmable gate array (FPGA) development boards I will be using throughout the semester. This involved assembling my board, initial testing, and implementing Verilog to control LEDs and a 7-segment display using Radiant, Segger Embedded Studio, and ModelSim.

More information on the lab requirements can be found on the [E155 Lab 1 Course Page](https://hmc-e155.github.io/lab/lab1/).

## Development Board: Soldering and Set up
The first step was to assemble the custom printed circuit board which hosts the MCU and FPGA boards. This involved sodering both surface mount technology (SMT) and through hole technology (THT) components, based on the provided [BOM.](https://hmc-e155.github.io/assets/doc/E155_v4_Dev_Board_BOM.html)

<!-- ![Completed E155 Development Board](/assets/images/lab1/SolderFront.jpeg)  -->

{% include figure popup=true image_path="/assets/images/lab1/SolderFront.jpeg" alt="Completed E155 Development Board" caption="Completed E155 Development Board" %}


After soldering, it was time to power up and test the board. To do so, I programmed the FPGA using Lattice Radiant and Segger Embedded Studio to toggle LED pins at predetermined frequencies. After confirming my board worked as expected, it was time to implement LEDs and the 7 segment display.

## Design & Implementation

### Lab Requirements
The next step was to program three LEDs and a seven segment display. The seven segment display is to read four DIP switch signals, s, as a 4 bit binary value and display that value in hexidecimal. The behavior of the LEDs are described by the following tables. 

<table class="caption-top table">
<thead>
<tr class="header">
<th>Signal Name</th>
<th>Signal Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><code>clk</code></td>
<td>input</td>
<td>48 MHz clock on FPGA</td>
</tr>
<tr class="even">
<td><code>s[3:0]</code></td>
<td>input</td>
<td>the four DIP switches (on the board, SW6)</td>
</tr>
<tr class="odd">
<td><code>led[2:0]</code></td>
<td>output</td>
<td>3 LEDs (you may use the on-board LEDs)</td>
</tr>
<tr class="even">
<td><code>seg[6:0]</code></td>
<td>output</td>
<td>the segments of a common-anode 7-segment display</td>
</tr>
</tbody>
</table>
<p>The following tables define the relationship of the LEDs to the switches and clock.</p>
<div class="center-table">
<table class="caption-top table">
<thead>
<tr class="header">
<th style="text-align: center;"><code>S1</code></th>
<th style="text-align: center;"><code>S0</code></th>
<th style="text-align: center;"><code>led[0]</code></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: center;">0</td>
<td style="text-align: center;">0</td>
<td style="text-align: center;">OFF</td>
</tr>
<tr class="even">
<td style="text-align: center;">0</td>
<td style="text-align: center;">1</td>
<td style="text-align: center;">ON</td>
</tr>
<tr class="odd">
<td style="text-align: center;">1</td>
<td style="text-align: center;">0</td>
<td style="text-align: center;">ON</td>
</tr>
<tr class="even">
<td style="text-align: center;">1</td>
<td style="text-align: center;">1</td>
<td style="text-align: center;">OFF</td>
</tr>
</tbody>
</table>
</div>
<div class="center-table">
<table class="caption-top table">
<thead>
<tr class="header">
<th style="text-align: center;"><code>S3</code></th>
<th style="text-align: center;"><code>S2</code></th>
<th style="text-align: center;"><code>led[1]</code></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: center;">0</td>
<td style="text-align: center;">0</td>
<td style="text-align: center;">OFF</td>
</tr>
<tr class="even">
<td style="text-align: center;">0</td>
<td style="text-align: center;">1</td>
<td style="text-align: center;">OFF</td>
</tr>
<tr class="odd">
<td style="text-align: center;">1</td>
<td style="text-align: center;">0</td>
<td style="text-align: center;">OFF</td>
</tr>
<tr class="even">
<td style="text-align: center;">1</td>
<td style="text-align: center;">1</td>
<td style="text-align: center;">ON</td>
</tr>
</tbody>
</table>
</div>
<div class="center-table">
<table class="caption-top table">
<thead>
<tr class="header">
<th style="text-align: center;"><code>led[2]</code></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: center;">Blink at 2.4 Hz</td>
</tr>
</tbody>
</table>
</div>

<!-- Explanation of design approach. How did you go about designing and implementing the design? -->
### Design
To organize my thoughts I used a block diagram to map the logic.

<!-- ![Lab 1 Block Diagram](/assets/images/lab1/Lab1BlockDiagram.png)  -->
{% include figure popup=true image_path="/assets/images/lab1/Lab1BlockDiagram.png" alt="Lab 1 Block Diagram" caption="Lab 1 Block Diagram" %}

#### Led Logic Design
The truth tables revealed that led[0] behaves as an XOR gate with inputs S1 and S0 and that led[1] behaves as an AND gate with inputs S3 and S2. 

To have led[2] to blink at 2.4 Hz, I utilized the internal 48 gHz high speed oscillator from the HSOSC Library. A frequency of 2.4 Hz would have a full cycle of 0.4167 second. Dividing this by the frequency of the internal oscillator, we get that a full cycle would require $2*10^7$ ticks. To achieve a duty cycle of 50%, I implemented a flip flop that switched led[2] every $10^7$ clicks. 

#### Seven Segment Logic Design
To interface the seven segment display with the board, I conferred with the [datasheet](https://www.jameco.com/Jameco/Products/ProdDS/335090.pdf) to determine resistor values. 
<!-- datasheet and resitor values: Calculations provided to demonstrate that the current draw for each segment in the seven-segment display is within recommended operating conditions. -->

<!-- ![Resistor Calculations for Seven Segment Display](/assets/images/lab1/resistorcalculations.jpeg)  -->
{% include figure popup=true image_path="/assets/images/lab1/resistorcalculations.jpeg" alt="Resistor Calculations for Seven Segment Display" caption="Resistor Calculations for Seven Segment Display" %}

I opted to use resistor values of 240 ohms, producing 6.25 mA of current. 

A wiring schematic is shown below. 
<!-- ![Lab 1 Circuit Schematic, Victoria Parizot, 09/04/2024](/assets/images/lab1/CircuitDiagram.jpeg)  -->
{% include figure popup=true image_path="/assets/images/lab1/CircuitDiagram.jpeg" alt="Lab 1 Circuit Schematic, Victoria Parizot, 09/04/2024" caption="Lab 1 Circuit Schematic, Victoria Parizot, 09/04/2024" %}


Here is a photo of the implemented design!
<!-- ![Completed Circuit](/assets/images/lab1/SevenSegments.jpeg)  -->
{% include figure popup=true image_path="/assets/images/lab1/SevenSegments.jpeg" alt="Completed Circuit" caption="Completed Circuit" %}

<!-- video of it working -->
## Testing
<!-- Explanation of testing approach. How did you verify your design was behaving as expected? -->
To verify that the design would work as expected, I ran simulations on ModelSim. To do, I instantiated a test bench that would test all 16 possible inputs of the dip switch to ensure the LED and seven segment display output as expected. 

<!-- ![Wave forms of test bench](/assets/images/lab1/wave2.png)  -->
{% include figure popup=true image_path="/assets/images/lab1/wave2.png" alt="Wave forms of test bench" caption="Wave forms of test bench" %}


I tested the blinking led[2] with the oscilliscope to confirm it had a frequency of 2.4 hz.
<!-- ![Frequency verification of led[2]](/assets/images/lab1/240HzLed%5B2%5D.png)  -->

{% include figure popup=true image_path="/assets/images/lab1/240HzLed%5B2%5D.png" alt="Frequency verification of led[2]" caption="Frequency verification of led[2]" %}


<!-- ModelSim simulation (either manually force or automatic testbench) to demonstrate that the design is working properly. -->

## Conclusion
<!-- Statement of whether the design meets all the requirements. If not, list the shortcomings. -->
<!-- Number of hours spent working on the lab are included. -->
In all, Lab 1 offered a cohesive introduction to the work flow for the coming labs. I was able to practice my sodering technique, interfacing with different software, assigning pins, and testing my design with ModelSim. 

The design meets all the requirements. I spent roughly 15 hours on this lab.

