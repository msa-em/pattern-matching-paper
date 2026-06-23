---
title: Data processing
numbering:
  enumerator: 3.%s
---

The full workflows are released open-source on github [@PMgithub]. 
One notebook is given for the model dataset, which details each step and is written both as a documentation and as a tutorial directed towards new users. 
Another more advanced notebook is released for the test dataset, which includes some additional options. 
All major data analysis steps are described with examples in the following. 

The SPED datasets were pre-processed using the open source libraries hyperspy [@hyperspy] and pyxem [@pyxem]. 
The pre-processing steps are schematically summarised in [](#fig_data_process), and consist of: 
(1.0) direct beam centring, (1.1) signal cropping and binning, (1.2) summation of half-patterns, (1.3) cross-correlating the patterns with a binary disk, and (1.4) thresholding the patterns. 

:::{figure} ./figures/data_processing.png 
:name: fig_data_process
:width: 65%
Schematic showing SPED data pre-processing, which includes (1.0) centring the direct beam in each PED pattern, (1.1) binning and cropping the signal to exclude periods shorter than the $\lbrace220\rbrace$ Al reflections, (1.2) summing half-patterns, (1.3) cross-correlating the patterns with a binary disk, and (1.4) thresholding the patterns. A representative T$_{1-2}$ pattern from the model dataset is displayed.
:::

[](#fig_preprocessing) presents an interactive figure where the pre-processing can be visualised for six representative patterns belonging to each category. 
The disk radius for step (1.3) can be explored, together with the threshold value for step (1.4). 
In this work the disk radius was set to 3 pixels and the threshold to 0.3.

:::{figure} #app:preprocessing
:name: fig_preprocessing
:placeholder: ./figures/preprocessing_placeholder.png
Interactive pre-porcessing of six representative patterns from the Al-Cu-Li model dataset that belong to each of the six categories. The top row shows the patterns after summation of half-patterns (1.2). The middle row presents the same patterns after cross-correlating them with a binary disk (1.3) with a user-selected radius. The bottom row displays the same patterns after thresholding (1.4) where all intensities that are below a user-selected threshold value are set to zero.
:::

The model dataset and the test dataset were pre-processed in the same way, with one exception. 
The difference was that the test dataset was subjected to an additional diffraction pattern averaging step prior to (1.3), to improve the signal-to-noise. 
For this, nearest neighbour patterns were averaged by using a Gaussian kernel with a standard deviation of 0.65. 
To ensure a fair comparison to the results in the previous study [@Thronsen2024], such averaging was not done on the model dataset. 
