---
permalink: /diffPrivacy/
title: "Improving Visual Utility of Differentially Private Scatterplots"
description: "Summer 2023 - My Research under Professor Anand D. Sarwate as part of the DIMACS program at Rutgers University"
---

## Introduction
In Summer 2023, I did research under [Professor Anand D. Sarwate](https://adsarwate.github.io/) as part of the Center for Discrete Mathematics and Theoretical Computer Science [(DIMACS)](https://reu.dimacs.rutgers.edu/) at Rutger University with a partnership with Charles University.

I worked on evaluating and improving the visual utility of differentially private data. During this time, I created a [Python framework](https://github.com/vparizot/DifferentialPrivacyVisualization) to generate differentially private scatterplots with different post-processing techniques based on user-chosen parameters and datasets. 

{% include figure popup=true image_path="/assets/images/diffP/DPProcess.png"  %}

I then used this framework to run an experiment on two CDC datasets to evaluate post-processing techniques on visual utility. Ultimately, I presented this research to peers and professors during the [Midsummer Combinatorial Workshop](https://www.mff.cuni.cz/en/kam/events/mcw/mcw-2023) at Charles University, Prague!

{% include figure popup=true image_path="/assets/images/diffP/researchOverview.png" %}


View the github repo with my final paper, final presentation, and code [here!](https://github.com/vparizot/DifferentialPrivacyVisualization) 

View the Blog I kept during research [here!](https://reu.dimacs.rutgers.edu/~mp2005/)

## Abstract
In data-driven research fields like healthcare and technology, access to sensitive individual information is crucial for generating valuable insights. However, privacy regulations pose challenges for publishing such data, hindering researchers’ access. Differential privacy has emerged as a promising solution, allowing researchers to learn from sensitive data while protecting individual privacy. This research focuses on generating differentially private scatterplots, a common data visualization tool, while retaining visual utility. The approach combines strategies of partitioning data, adding calibrated noise, and post-processing to suppress noise. The study explores factors like ε (privacy level), algorithms, bin size, data distribution, and sample size to understand their impact on visual utility. Two small datasets are used, derived from the US Census and World Health Organization, with direct application for Differential Privacy. The results highlight the trade-offs between privacy and visualization integrity, aiding researchers in making informed decisions to balance privacy and data visualization accuracy. Future directions include exploring more sophisticated point regeneration techniques and integrating differentially private heatmaps techniques to improve visual accuracy

## Acknowledgements
I would like to acknowledge the NSF for supporting my research this summer under grant CNS-2150186, as well as the DIMACS program for the opportunity to research.
{% include figure popup=true image_path="/assets/images/diffP/dimacs_logo.gif" caption="" %}



