---
title: Methods
---

The full workflows are released open-source on github [@PMgithub]. 
One notebook is given for the model dataset, which details each step and is written both as a documentation and as a tutorial directed towards new users. 
Another more advanced notebook is released for the test dataset, which includes some additional options. 
All major data analysis steps are described with examples in the following. 

## Data collection

Before data collection, the Al matrix was oriented to $\langle001\rangle$ zone axis. 
SPED was performed using a JEOL JEM-2100F operated at 200 kV in nanobeam diffraction mode. 
A NanoMegas scan generator and precession system were used with a precession frequency of 100 Hz. 
The SPED datasets were collected on a 256$\times$256 pixels Medipix3 MerlinEM direct electron detector from Quantum Detectors with the bit mode set to 2$\times$12-bit. 

The model dataset from the Al-Cu-Li system was collected for a previous publication [@Thronsen2024] and was in this work retrieved from the open data repository Zenodo [@Thronsen2022zenodo]. 
For this dataset, the nominal probe size was set to 1.3 nm, the exposure time per pattern was set to 10 ms, and the step size was set to 4.6 nm. 
The convergence semi-angle and precession angle were measured to 1.1 mrad and 1.0&deg; (17.5 mrad), respectively. 
A schematic figure of the data collection is presented in Figure [](#fig_preprocessing)(a), which shows the ground truth phase map together with six representative unique diffraction patterns from the various phases in this alloy. 

:::{figure} ./figures/data_collection_preprocessing.png 
:name: fig_preprocessing
(a) Schematic figure showing SPED data collection in the Al-Cu-Li model alloy system. The TEM specimen is represented by the ground truth phase map, and six unique PED patterns are displayed. (b) Schematic showing SPED data pre-processing, which includes (1.0) centring the direct beam in each PED pattern, (1.1) binning and cropping the signal to exclude periods shorter than the $\lbrace220\rbrace$ Al reflections, (1.2) summing partly overlapping half-patterns, (1.3) cross-correlating the patterns with a binary disk, and (1.4) thresholding the patterns. 
:::

The test dataset from the Al-Mg-Si-Cu alloy was collected specifically for this work and has been made avaibale open source via Zenodo [@Zenodo2024]. 
The nominal probe size was 0.5 nm, the exposure time per pattern was 40 ms, and the step size was 1.4 nm. 
The precession angle was measured to 0.53&deg; (9.3 mrad). 
To complement the SPED phase mapping, atomically resolved high-angle annular dark-field (HAADF) STEM images were collected from some of the same precipitates that were included in the SPED test dataset. 
For this, a JEOL JEM ARM200F microscope was operated at 200 kV, and an annular Gatan detector with inner and outer collection angles of 51 and 203 mrad, respectively, was used. 
The images were post-processed to reduce noise by blurring and enhance contrast, by applying a circular and centred band-pass mask (radius $\approx$1.3-1.8 Å$^{-1}$) to the fast Fourier transform (FFT) patterns of the images, before calculating the inverse FFT. 
The HAADF-STEM images were manually labelled based on pre-knowledge of the atomic strcutures of precipitate phases contained within this particular alloy [@Sunde2020]. 

## Data processing

The SPED datasets were pre-processed using the open source libraries hyperspy and pyxem [@hyperspy; @pyxem]. 
The pre-processing steps are schematically summarised in Figure [](#fig_preprocessing)(b), and consist of: 
(1.0) direct beam centring, (1.1) signal cropping and binning, (1.2) summation of half-patterns, (1.3) cross-correlating the patterns with a binary disk, and (1.4) thresholding the patterns. 
The model dataset and the test dataset were pre-processed in the same way, with one exception. 
The difference was that the test dataset was subjected to an additional diffraction pattern averaging step prior to (1.3), to improve the signal-to-noise. 
For this, nearest neighbour patterns were averaged by using a Gaussian kernel with a standard deviation of 0.65. 
To ensure a fair comparison to the results in the previous study [@Thronsen2024], such averaging was not done on the model dataset. 
