---
title: Data collection
numbering:
  enumerator: 2.%s
---

Before data collection, the Al matrix was oriented to $\langle001\rangle$ zone axis. 
SPED was performed using a JEOL JEM-2100F operated at 200 kV in nanobeam diffraction mode. 
A NanoMegas scan generator and precession system were used with a precession frequency of 100 Hz. 
The SPED datasets were collected on a 256${\times}$256 pixels Medipix3 MerlinEM direct electron detector from Quantum Detectors with the bit mode set to 2${\times}$12-bit. 

The model dataset from the Al-Cu-Li system was collected for a previous publication [@Thronsen2024] and was in this work retrieved from the open data repository Zenodo [@Thronsen2022zenodo]. 
For this dataset, the nominal probe size was set to 1.3 nm, the exposure time per pattern was set to 10 ms, and the step size was set to 4.6 nm. 
The convergence semi-angle and precession angle were measured to 1.1 mrad and 1.0&deg; (17.5 mrad), respectively. 
A schematic figure of the data collection is presented in [](#fig_data_collect), which shows the ground truth phase map together with six representative unique diffraction patterns from the various phases in this alloy. 

:::{figure} ./figures/data_collection.png 
:name: fig_data_collect
:width: 333px
Schematic figure showing SPED data collection in the Al-Cu-Li model alloy system. The TEM specimen is represented by the ground truth phase map, and six unique PED patterns are displayed. 
:::

The test dataset from the Al-Mg-Si-Cu alloy was collected specifically for this work and has been made available open source via Zenodo [@Sorhaug2024zenodo]. 
The nominal probe size was 0.5 nm, the exposure time per pattern was 40 ms, and the step size was 1.4 nm. 
The precession angle was measured to 0.53&deg; (9.3 mrad). 

To complement the SPED phase mapping, atomically resolved high-angle annular dark-field (HAADF) STEM images were collected from some of the same precipitates that were included in the SPED test dataset. 
For this, a JEOL JEM ARM200F microscope was operated at 200 kV, and an annular Gatan detector with inner and outer collection angles of 51 and 203 mrad, respectively, was used. 
The images were post-processed to reduce noise by blurring and enhance contrast, by applying a circular and centred band-pass mask (radius $\approx$1.3-1.8 Å$^{-1}$) to the fast Fourier transforms (FFTs) of the images, before calculating the inverse FFTs. 
The HAADF-STEM images were manually labelled based on pre-knowledge of the atomic structures of precipitate phases contained within this particular alloy [@Sunde2020]. 