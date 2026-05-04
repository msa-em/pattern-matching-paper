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
A schematic figure of the data collection is presented in Figure 1(a), which shows the ground truth phase map together with six representative unique diffraction patterns from the various phases in this alloy. 

\setkeys{Gin}{width=.8\linewidth}
![](./figures/initial_processing.png "(a) Schematic figure showing SPED data collection in the Al-Cu-Li model alloy system. The TEM specimen is represented by the ground truth phase map, and six unique PED patterns are displayed. (b) Schematic showing SPED data pre-processing, which includes (1.0) centring the direct beam in each PED pattern, (1.1) binning and cropping the signal to exclude periods shorter than the $\lbrace220\rbrace$ Al reflections, (1.2) summing partly overlapping half-patterns, (1.3) cross-correlating the patterns with a binary disk, and (1.4) thresholding the patterns.")

The test dataset from the Al-Mg-Si-Cu alloy was collected specifically for this work and has been made avaibale open source via Zenodo [@Zenodo2024]. 
The nominal probe size was 0.5 nm, the exposure time per pattern was 40 ms, and the step size was 1.4 nm. 
The precession angle was measured to 0.53&deg; (9.3 mrad). 
To complement the SPED phase mapping, atomically resolved high-angle annular dark-field (HAADF) STEM images were collected from some of the same precipitates that were included in the SPED test dataset. 
For this, a JEOL JEM ARM200F microscope was operated at 200 kV, and an annular Gatan detector with inner and outer collection angles of 51 and 203 mrad, respectively, was used. 
The images were post-processed to reduce noise by blurring and enhance contrast, by applying a circular and centred band-pass mask (radius $\approx$1.3-1.8 Å$^{-1}$) to the fast Fourier transform (FFT) patterns of the images, before calculating the inverse FFT. 
The HAADF-STEM images were manually labelled based on pre-knowledge of the atomic strcutures of precipitate phases contained within this particular alloy [@Sunde2020]. 


## Data processing

The SPED datasets were pre-processed using the open source libraries hyperspy and pyxem [@hyperspy; @pyxem]. 
The pre-processing steps are schematically summarised in Figure 1(b), and consist of: 
(1.0) direct beam centring, (1.1) signal cropping and binning, (1.2) summation of half-patterns, (1.3) cross-correlating the patterns with a binary disk, and (1.4) thresholding the patterns. 
The model dataset and the test dataset were pre-processed in the same way, with one exception. 
The difference was that the test dataset was subjected to an additional diffraction pattern averaging step prior to (1.3), to improve the signal-to-noise. 
For this, nearest neighbour patterns were averaged by using a Gaussian kernel with a standard deviation of 0.65. 
To ensure a fair comparison to the results in the previous study [@Thronsen2024], such averaging was not done on the model dataset. 

## Defining templates

Three approaches of defining template patterns were used for the model dataset, as presented schematically in Figure 2 and explained in the following. 
For the model system, it was observed that some precipitates frequently overlapped in projection. 
To accomodate for this, overlap patterns can be created by simply taking the average of each pair of dissimilar template patterns and rescaling the intensity. 
These overlap templates corresponding to two phases and/or orientations can be included in the template bank in the same manner as for the single crystal template patterns. 
This option is included in the advanced notebook only, to demonstrate the flexibility of the methodology, and overlap patterns are not included when comparing to the ground truth. 

For the test system, only the machine learning-based approach (C) was used to define template patterns since the unique diffraction patterns are not known in advance. 

\setkeys{Gin}{width=.8\linewidth}
![](./figures/template_selections.png "Schematic illustration of the three approaches used to define template patterns: (a) simulate patterns, (b) manually select regions with unqiue patterns, or (c) use NMF to find regions with unqiue patterns.")

#### (A) Simulations: 
The five expected unique diffraction patterns were kinematically simulated using the open-source python library diffsims [@diffsims], based on the known crystal structures (Table S-II) and expected orientation relationships [@Thronsen2024]. 
The simulated Bragg spots were expanded to trapezoid disks, using the astropy python library [@astropy], to more closely resemble the Bragg disks in the recorded patterns. 
The simulated patterns were thereafter pre-processed in the same manner as the experimental patterns, as previously described.

#### (B) Manual selection: 
The five template patterns were defined by averaging experimental diffraction patterns in the SPED dataset over five manually selected regions in real space. 
These regions were chosen based on manually recognising the known and distinct morphologies of each precipitate type in a virtual dark-field (VDF) image. 
This VDF image was created by applying a mask that blocked out the Al matrix reflections and then summing the intensity in each PED pattern. 

#### (C) NMF-guided selection:
NMF was performed on the pre-processed dataset using the scikit-learn implementation in hyperspy [@sklearn; @hyperspy]. 
A signal mask was applied to exclude Al reflections. 
The use of the signal mask, and especially the specific pre-processing done here, significantly reduced the random acess memory required to run the NMF algorithm. 
The result of NMF is known to be highly sensitive to the number of chosen output components [@Martineau2019; @Bergh2020; @Thronsen2024]. 
Therefore, singular value decomposition was computed prior to NMF, and the corresponding scree plot, which shows the fraction of total variance accounted for by each component, was studied to find a ballpark for an adequate number of components. 
Afterwards, NMF was run several times, both with a lower and a higher number of components than the value estimated based on the scree plot, and the results were inspected manually, before a final number of components was selected. 
The resulting components were manually categorised based on the unique precipitate patterns they belonged to. 
The NMF loading maps were thresholded, and for each loading map, the 10\% highest values were taken to define unique regions in real space. 
Within each unique region, patterns were extracted from the pre-processed dataset and summed to give the final template patterns. 
This means that the NMF results were not used as templated directly; NMF was rather used to guide the choice of unique regions, and the template patterns were extracted from the pre-processed SPED dataset itself. 

## Pattern matching
The major steps in the pattern matching workflow after pre-processing is schematically presented in Figure 3 for the model dataset. 
After defining template patterns (step 2.0), matching is performed by calculating the Normalised cross-correlation (NCC) score to all the template patterns, for each pre-processed PED pattern in the SPED dataset (step 2.1). 
The NCC match score is defined as \cite{NCC}: \hl{Obs! sum-tegnet mangler...}
\begin{align}
    \frac{\sum_{k_x,k_y}\left[I_{\text{Pat.}}(k_x,k_y)-\overline{I_{\text{Pat.}}}\right]\left[I_{\text{Temp.}}(k_x,k_y)-\overline{I_{\text{Temp.}}}\right]}{\sqrt{\sum_{k_x,k_y}\left[I_{\text{Pat.}}(k_x,k_y)-\overline{I_{\text{Pat.}}}\right]^2\sum_{k_x,k_y}\left[I_{\text{Temp.}}(k_x,k_y)-\overline{I_{\text{Temp.}}}\right]^2}},
\end{align}
where $I_\text{p}(k_x,k_y)$ and $I_\text{t}(k_x,k_y)$ are the intensities of a pre-processed PED pattern and a template pattern, respectively, and $\overline{I_\text{p}}$ and $\overline{I_\text{t}}$ are their respective average intensities. 
Only intensities included within a signal mask are included in this NCC calculation. 
The signal mask blocks out the direct beam region, the Al Bragg disks and higher scattering angles, so that these regions are not considered. 
% intensity at pixel $(k_x,k_y)$, respectively

\setkeys{Gin}{width=.8\linewidth}
![](./figures/PM.png "Schematic workflow of pattern matching: (2.0) Define template patterns, (2.1) match each pattern with all the templates within a signal-masked region, (2.2) label patterns according to the match scores, and (2.3) identify unlabelled patterns that can be used as basis for defining new templates.")

After calculating the match scores, the patterns are labelled to produce a phase map (step 2.2). 
This is normally done by assigning the phase corresponding to the highest NCC score. 
Phase labelling was also done using the same prioritisation scheme as in the previous work [@Thronsen2024], to ensure a fair comparison between the model system phase map and the ground truth. 
To report a quantitative similarity metric, the phase mapping accuracy was defined as the percentage of patterns for which the phase labelling in the resulting phase map was identical to that in the ground truth. 

The map of the highest NCC scores per probe position is inspected to identify low maximum NCC scores and thereby patterns that do not resemble any of the template patterns to a sufficient degree. 
The NCC score map is thresholded to reveal the lowest NCC scores, and additional templates can then be searched for within these low match score regions (step 2.3). 
This option is included in the advanced notebook for the model system which presents two ways of finding additional templates; NMF (as explained earlier) and a density-based clustering algorithm. 

For the test system, additional templates were sought after using NMF. 
To capture all of the unique pattern types, the cycle of matching and searching for additional templates was repeted three times. 
In addition, since the L phase patterns closely resemble those from the C phase, the patterns initially labelled as L or C were manually re-inspected to verify correct labelling. 
If L or C patterns had been mislabelled as C or L respectively, that C or L pattern was added to the template bank before the matching was redone and the phase map updated. 
