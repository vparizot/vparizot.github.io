---
permalink: /gokart/
title: "Shopping Kart Go Kart"
description: "Designing and building an electric gokart"
header:
  overlay_image: assets/images/gokart/gokart1.jpeg
  overlay_filter: 0.3
  actions:
    - label: "Project Website"
      url: "https://shoppinggokart.github.io/mechdesignwebsite/"
#   caption: "Debugging DMA"

excerpt: >
  
  <br />
  <br />


---

## Introduction and Project Background
The goal for this project was to create a functional go-kart vehicle. The Ferrari GK is a go-kart built around a shopping cart frame and a 1 HP motor and includes functional steerage, braking, and acceleration. The acceleration and direction that the vehicle propels is controlled by a PWM controller, and is powered by two 12V car batteries. An emergency stop function is also included in order to improve the safety of the vehicle. 

A demo of our final project is here:
<!-- {{<video https://youtu.be/s2t5OHpjwbU>}}  -->

{% include video id="s2t5OHpjwbU" provider="youtube" %}

Look at our projects final website [here.](https://shoppinggokart.github.io/mechdesignwebsite/){:target="_blank"}

## Requirements & Specifications
<!-- Requirements and Specifications (i.e., what does the design need to do?)
Highlights and justifies clear quantitative and qualitative requirements and specifications for the design -->
In order to make sure our go kart will work, our group defined a series of requirements and specifications. These requirements and specifications are motivated by safety and what we decided as critical in a functional go kart. These requirements and specifications assume that the user is within the weight constraint and all limbs are within the bounds of the cart. A list of those details is below:

### Requirements
- Must be safe to use for user
- Must include steering wheel and be steerable by user
- Must include a working brake
- Must be powered with motor
- Must include speed control
- Must be able to move user 5 MPH
- Must be able to move a 200lb user

### Specifications
- The cart must be able to safely transport a user of 200lbs at least 10 ft, with the ability to accelerate at 1m/s^2 up to 5 MPH. 
- Implement functional steerage, controlled by a steering wheel, on the front wheels with a spindle assembly. 
- Implement functional braking on the rear wheels 
<!-- - Achieve a speed of at least 5 MPH for a 200 lb user -->


## Design Features of Main Subsystems
Our go kart consists of five critical subsystems: steerage, frame, braking, motor, and PWM control. These subsystems are critical in allowing the user to control the go kart. The steerage subsystem allows the users to control the direction of the vehicle. The brake subsystem allows the user to halt movement. The motor and PWM control subsytems allows the user to contol their speed. The frame is critical in holding the user, and combining all the other subsystems.

Read more about sub systems [here](https://shoppinggokart.github.io/mechdesignwebsite/designfeatures.html){:target="_blank"}

## Evaluation of Design
To motivate and verify our design decisions, a handful of analysis around each subsytem was performed. This allows us to ensure the use and safety of our design.

Read more about the evaluation of our design [here](https://shoppinggokart.github.io/mechdesignwebsite/evaluationofdesign.html){:target="_blank"}

## Future Work
<!-- Presents clear and specific directions for future work -->
During the engineering process, there were a few design decisions the team made due to budget and time constraints. In order to improve our current vehicle, we would want to improve the overall stability of the frame to support users of greater weight by replacing our 80-20 frame with steel. In addition, we would want to attempt to increase the speed of the vehicle by increasing the input voltage of the motor with higher voltage batteries. We would also want to improve user comfort by using a larger shopping cart, and potentially including a seat. Finally, in future iterations we would want to make the steering differential, which would allow the vehicle to adjust to speed changes as it is making turns. 


## Conclusion
<!-- Clearly summarizes key takeaways from project and recommendations for future work -->

Overall, our team was able to succesfully build a vehicle that can safely transport a 200 pound user up to 5mph with 1 m/s^2 of acceleration. In addition, the vehicle contains a functional steering system and speed control that allows the user to moderate the vehicle's movement with ease. 


Throughout this project, the team grew comfortable with vehicle design -- learning common ways go-karts implement steering and how to integrate an electrical design. Beyond experience with vehicle design, the team applied our analysis skills to evaluate our design, getting experience with comparing design options and identifying potential areas of failure. This includes throught exercises on material design, fastners, and chain and sprocket design. The team also gained technical skills -- improving our machining skills and learning the MIG weld. The practice of CADing our entire system familiarized ourselves with a CAD workflow and more complex SolidWorks functionalities. Moreover, this project provided more experience in project management and practice in the iterative design process. 

If we were to do this project again, there are a handful of changes we would make as detailed above. We would consider steel for the frame, use a larger shopping cart, and relook at steerage design. As we conclude our project we have a better idea of how all these subsystems work together. If we were to design another vehicle or mechanical project in the future, our experiences will be immensely helpful in the design process.

We are excited about the outcome of our project, and look forward to riding it around Harvey Mudd's campus!

## Acknowledgements
We would like to thank Professor Mendleson and Drew Price for their help and guidance throughout the project. We would also like to thank Jacob, Xavier, Lynn, and MACH for their help acquiring materials and implementing ideas. 
