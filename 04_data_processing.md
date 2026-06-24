---
title: Data processing
numbering:
  enumerator: 3.%s
---

The full data analysis workflows are released open-source on GitHub [@PMgithub], and they are based on the open source python libraries HyperSpy [@hyperspy] and pyxem [@pyxem]. 
The notebooks explain each step in the analysis of the model dataset, and they are written both as a documentation and as a tutorial directed towards new users. 
The notebooks inlude one pre-processing notebook (1), one simple version of the PM workflow (2A) with comparisons to ground truth, and one more advanced PM notebook (2B) that includes additional options but no comparison to ground truth [@PMgithub]. 
All major data analysis steps are described with examples in the following. 

The pre-processing steps are schematically summarised in [](#fig_data_process), and consist of: 
(1.0) direct beam centring, (1.1) signal binning and cropping to exclude periods shorter than the $\lbrace220\rbrace$ Al reflections, (1.2) summation of half-patterns, (1.3) cross-correlating the patterns with a binary disk, and (1.4) thresholding the patterns. 
Centering the direct beam in (1.0) is a mandatory first step, while steps (1.1) and (1.2) greatly reduce the data size and increase the signal-to-noise ratio. 
Template matching the patterns with a binary disk (1.3) effectively enhances each Bragg disk, which makes it a beneficial step prior to thresholding or prior to peak finding to locate Bragg disks, as has also been noted in previous work [@Savitsky2021; @Francis2024]. 
In the last step (1.4) all intensities below a manually set threshold value are set to zero. 

:::{figure} ./figures/data_processing.png 
:name: fig_data_process
:width: 65%
Schematic showing SPED data pre-processing, which includes (1.0) centring the direct beam in each PED pattern, (1.1) binning and cropping the patterns, (1.2) summing half-patterns, (1.3) cross-correlating each pattern with a binary disk, and (1.4) thresholding the patterns. A representative T$_{1-2}$ pattern from the model dataset serves as a representative example pattern.
:::

[](#fig_preprocessing) presents an interactive figure where the two last pre-processing steps can be visualised for six representative patterns that belong to each category. 
The disk radius for step (1.3) can be explored, together with the threshold value for step (1.4). 
In this work the disk radius was set to 3 pixels and the threshold to 0.3.

:::{figure} #app:preprocessing_widget
:name: fig_preprocessing
:placeholder: ./figures/preprocessing_placeholder.png
Interactive pre-porcessing of six representative patterns from the Al-Cu-Li model dataset. The top row shows the patterns after summation of half-patterns (1.2), plotted on log scale. The middle row presents the same patterns after cross-correlating them with a binary disk (1.3) with a user-selected radius. The bottom row displays the same patterns after thresholding (1.4), where all intensities that are below a user-selected threshold value are set to zero.
:::

The model dataset and the test dataset were pre-processed in the same way, with one exception. 
The difference was that the test dataset was subjected to an additional diffraction pattern averaging step prior to (1.3), to improve the signal-to-noise further. 
For this, nearest neighbour patterns were averaged by using a Gaussian kernel with a standard deviation of 0.65. 
To ensure a fair comparison to the results in the previous study [@Thronsen2024], such averaging was not done on the model dataset. 
