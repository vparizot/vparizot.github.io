---
permalink: /digital-design/
title: "Digital Design Showcase"

layout: single
author_profile: True

header:
  overlay_image: assets/images/fotos/VIC_5033.jpg
  overlay_filter: 0.3
  actions:
    - label: "Datasheets"
      # icon: "fab fa-fw fa-linkedin"
      url: "/resources/"
#   caption: "Debugging DMA"

excerpt: >
  These project use an UPduino v3.1 (iCE40 UP5K) FPGA and a STM32 Nucleo-32 (STM32L432KC) MCU board
  


sidebar:
  - title: "In-Progress Images"

  - image: assets/images/microPDemo/VIC_5528.jpg
    image_alt: "image0"

  - image: assets/images/IMG_2005.jpeg
    image_alt: "image1"
  - 
    image: assets/images/microPDemo/IMG_16.jpg
    image_alt: "image8"
  - 
    image: assets/images/DD.png
    image_alt: "image2"
  - 
    image: assets/images/microPDemo/PariVo.JPEG
    image_alt: "image3"
  - 
    image: assets/images/microPDemo/IMG_12.jpg
    image_alt: "image4"
  - 
    image: assets/images/microPDemo/IMG_10.jpg
    image_alt: "image5"
  - 
    image: assets/images/microPDemo/IMG_4.jpg
    image_alt: "image6"
  - 
    image: assets/images/microPDemo/IMG_08.jpg
    image_alt: "image7"
  - 
    image: assets/images/microPDemo/IMG_15.jpg
    image_alt: "image9"
  - 
    image: assets/images/microPDemo/IMG_13.jpg
    image_alt: "image10"
  - 
    image: assets/images/microPDemo/VIC_5525.jpg
    image_alt: "image11"
  


feature_row:

  - image_path: /assets/images/lab6/DS1Z_QuickPrint11.png
    alt: "Temperature IoT"
    
    title: "Temperature IoT"
    excerpt: "IoT device to measure temperature and display on webserver, using UART & SPI."
    url: "/IoTProject/"
    btn_class: "btn--primary"
    btn_label: "Learn More"

  - image_path: assets/images/lab7/aes_cor_tb_success.PNG
    alt: "AES Encryption"
    title: "AES Encryption"
    excerpt: "Constructing a hardware accelerator for 128-bit Advanced Encryption Standard."
    url: "/AESEncryptionProject/"
    btn_class: "btn--primary"
    btn_label: "Learn More"

  - image_path: /assets/images/lab5/quadrature_encoder.gif
    alt: "Interrupts"
    title: "Interrupts"
    excerpt: "Implementation of MCU Interrupts to characterize a motor."
    url: "/interruptProject/"
    btn_class: "btn--primary"
    btn_label: "Learn More"

  - image_path: /assets/images/lab3/lab3header.jpeg
    alt: "Keypad Scanner"
    title: "Keypad Scanner"
    excerpt: "A deep dive into FSMs."
    url: "/FSMProject/"
    btn_class: "btn--primary"
    btn_label: "Learn More"

  - image_path: /assets/images/lab2/completedLab2.jpeg
    alt: "Multiplexed 7-Segment Display"
    title: "Multiplexed Display"
    excerpt: "An introduction to multiplexing with seven segment displays."
    url: "/multiplexingProject/"
    btn_class: "btn--primary"
    btn_label: "Learn More"

  - image_path: /assets/images/lab4/TIM16BlockDiagram.png
    alt: "Digital Audio"
    title: "Digital Audio"
    excerpt: "An exploration of MCU timers to play music."
    url: "/timersProject/"
    btn_class: "btn--primary"
    btn_label: "Learn More"

  - image_path: /assets/images/lab1/SolderFront.jpeg
    alt: "MCU and FPGA Set UP"
    title: "MCU and FPGA Set UP"
    excerpt: "A mix of SMT&THT soldering and setting up the boards."
    url: "/setup/"
    btn_class: "btn--primary"
    # btn_class: ".btn--small"
    btn_label: "Learn More"
    

---
## Two-Channel DJ Mixer


![image](/assets/images/microPDemo/PariVo.JPEG){: style="float: left"}

<sub> I made a two-channel DJ Mixer that controls the frequency and gain of AUX audio based on user inputs. Audio is read into the iCE40 FPGA through I2S commuication with an external PCM1808 ADC. We achieved lowpass and highpass filters in simulation using Finite Impulse Response (FIR) Filters and through hardware using RC circuits. The audio is then passed into the STM32 MCU using SPI, where the onboard DAC Peripheral with Direct Memory Access (DMA) outputs the manipulated audio to speakers. I got a lot of experience debugging and testing, making heavy use of the logic analyzer to visualize serial communication and the oscilliscope to view the audio wave forms. </sub>
<!-- ![DJ Mixer](/assets/images/microPDemo/PariVo.JPEG){: .align-left} -->

To learn more about the project, check out the project website: 

<a href="https://projectparivo.github.io/ProjectParivoPortfolio/" 
   class="btn btn--primary" 
   target="_blank" 
   rel="noopener noreferrer">
   Learn more about Project PariVo
</a>

## More Projects!

{% include feature_row type = "left"%}


