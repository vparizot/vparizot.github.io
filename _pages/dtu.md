---
permalink: /turbine/
title: "HAWC2, spin on that thang"
description: "Vertical-Axis Wind Turbine Clinic Project"
header:
  overlay_image: assets/images/DTU/pickup3.png
  overlay_filter: 0.3
  actions:
    - label: "Source Code"
      url: "https://github.com/vparizot/DTUHWU-DAQ"


excerpt: >
 Building and testing a Vertical-Axis Wind Turbine
 <br>
 <br>
 <br>
 <br>

---

## Project Summary
For my senior clinic project, a small group of my peers and I collaborated with Denmark Technical University and Heriot-Watt University to collect data on and increase the power generation capabilities of a Vertical-axis wind turbine (VAWT) for Malaysia deployment. Malaysia has low wind speeds of 3-5 m/s. Usually, for low wind speed applications, the turbine is scaled up. However, as part of the deliverable would be to transport the turbine on a plane, we had a constraint on maximum length of the blades to 6 feet. Thus, we faced a difficult problem of building a small turbine capable of generating power in these low wind speeds. 

{% include figure popup=true image_path="/assets/images/DTU/dtuFlow.png" caption="Block Diagram for Power Electronics and Sensors Circuit" %}


## Data Acquisistion System
I was in charge of building the data aquisition system to quantify the conditions our VAWT was subjected to and how it performed. The DAQ combined a 5A Hall effect current sensor in series with the battery, an anemometer to measure wind speed, and a wind vane to measure wind direction. A Teensy 4.0 was used to log the data from the sensors and a Matlab script was used for visualization. 

The code can be found on my [github](https://github.com/vparizot/DTUHWU-DAQ)

{% include figure popup=true image_path="/assets/images/DTU/circuitDTU.png" caption="DAQ Circuit Schematic" %}


## Pickup Truck Testing
Perhaps the most fun, and rewarding, aspect of this project was strapping our turbine to the back of a pick up truck for testing. The VAWT was mounted on a pickup truck and driven at speeds ranging from 15 to 45 mph. This setup provided consistent wind exposure, enabling the VAWT to reach the necessary tip speed ratios (TSRs) and power coefficients (CP) to generate up to 2 A of current for charging a 12V battery.

{% include figure popup=true image_path="/assets/images/DTU/pickup1.jpeg" caption="Pickup Truck Testing" %}

{% include figure popup=true image_path="/assets/images/DTU/pickup3.png" caption="Pickup Truck Testing" %}

The pick-up truck testing allowed the team to see at what wind speed the VAWT is able to generate current into the battery. Current into the battery implies power generation, proportional to the current and voltage going into the battery from the MPPT. Data from the DAQ 

{% include figure popup=true image_path="/assets/images/DTU/pickupTrial12.png" caption="Current and Wind Speed Data" %}

{% include figure popup=true image_path="/assets/images/DTU/pickupTrial19.png" caption="Current and Wind Speed Data When Varying Speeds" %}


## Summary 
During our simulation, we successfully achieved self-starting at our target wind speeds of 3 to 5 meters per second. However, we observed that power generation didn't begin until wind speeds reached approximately 10 to 15 meters per second. In testing, we saw a strong correlation between wind speed and current output, which helped validate our MPPT functionality, current sensing setup, and overall generator efficiency.

Based on these results, we've identified several key areas for improvement: First, reinforcing the shaft-to-gear connection to prevent mechanical slippage. Second, calibrating the wind vane to improve directional data accuracy. And third, addressing center shaft deflection to ensure mechanical stability and better power transfer.

Our project are summarized in our poster:

<!-- <object data="/assets/images/DTU/DTU_poster.pdf" type="application/pdf" width="100%" height="100%"></object> -->


<object data="/assets/images/DTU/DTU_poster.pdf" type="application/pdf" width="100%" height="100%">
    <p>It appears you don't have a PDF plugin for this browser.
    No biggie... you can <a href="/assets/images/DTU/DTU_poster.pdf">click here to
    download the PDF file.</a></p>
</object>
