---
title: Template patterns
numbering:
  enumerator: 4.%s
---

Three approaches of defining template patterns (A-C) were used for the model dataset, as explained in the following. 
For the test system, only the machine learning-based approach (C) was used since this dataset contains both patterns from known crystal structures ([](#table2)) and patterns from disordered structures that were not known in advance. 

## (A) Simulations
The five expected precipitate diffraction patterns were kinematically simulated using the open-source python library diffsims [@diffsims], based on the known crystal structures ([](#table1)) and orientation relationships [@Thronsen2024]. 
The simulated Bragg spots were expanded to trapezoid disks, using the astropy python library [@astropy], to more closely resemble the Bragg disks in the recorded patterns. 
A notebook that includes all the steps in the simulation process is included in the GitHub repository [@PMgithub]. 
The simulated patterns were pre-processed in the same manner as the experimental patterns, as previously described. 
[](#fig_templates_A) illustrates the two main steps of simulation and pre-processing and presents the final templates. 

:::{figure} ./figures/template_selections_A.png 
:name: fig_templates_A
Illustration of defining template patterns by approach (A) simulations, which includes kinematic simulations and pre-processing. The final template patterns are shown to the right. 
:::

## (B) Manual selection
Five real-space regions were drawn manually, and the pre-processed SPED dataset was averaged over each of these regions to yield five template patterns. 
The regions were chosen based on pre-knowledge of the known and distinct morphologies of each precipitate type and recognising these morphologies in a virtual annular dark-field (VADF) image. 
The VADF image was created by applying a mask that blocked out the direct beam and the Al matrix reflections and then summing the intensity in each PED pattern. 
[](#fig_templates_B) shows the VADF image with the selected regions, alongside the templates.

:::{figure} ./figures/template_selections_B.png 
:name: fig_templates_B
Illustration of defining template patterns by approach (B) manual selection, which involves manually selecting five regions with unique patterns based on the morphologies in the VADF image. The pre-processed SPED dataset was averaged over each region to yield the template patterns shown to the right. 
:::

## (C) NMF-guided selection
NMF was performed on the pre-processed dataset using the scikit-learn [@sklearn] implementation in hyperspy [@hyperspy]. 
A signal mask was applied to exclude the direct beam, the Al reflections and signals at higher scattering angles. 
In addition, a navigation mask was used to exclude real-space regions with patterns that did not show any other reflections than those from Al, as determined based on peak finding. 
Applying the masks and the specific pre-processing routine described earlier significantly reduce the data size and complexity, which in turn reduces the random-access memory required to run the NMF algorithm. 

The NMF result is known to be highly sensitive to the number of chosen output components [@Martineau2019; @Bergh2020; @Allen2021]. 
Therefore, singular value decomposition was computed prior to NMF, and the corresponding scree plot, which shows the fraction of total variance accounted for by each component, was inspected to find an adequate first estimate. 
NMF was run several times, both with a lower and a higher number of components than the first estimate, and the results were inspected manually before a final number was selected. 
[](#fig_nmf) presents an interactive plot where the NMF output for the model dataset is displayed for a user-selected number of components in the range of 1 to 20. 
Five components were chosen since these adequately describe the five unique precipitate patterns. 
A lower number failed to include all categories, while a higher number lead to signals belonging to the same category being split across various components. 
For the test system, it was less straightforward to find a suitable number since this system contains more precipitate categories and some highly similar unique patterns. 
After inspection of NMF results for a range of number of components, 27 components were chosen for the test system dataset. 
It must be underlined that although the number of components is important, searching for an optimal number of components is unnecessary within this workflow. 
As long as the number of components is high enough so that all the unique patterns are represented in separate components, templates can be found by NMF-guided selection, as described in the following. 

:::{figure} #app:nmf_components_widget
:name: fig_nmf
:placeholder: ./figures/nmf_placeholder.png
Interactive plot showing NMF results for the model dataset. Loadings and factors are shown for a user-selected number of components in the range of 1 to 20. The navigation and signal masks are displayed in white on the loadings and factors, respectively. 
:::

The process of NMF-based template selection is illustrated in [](#fig_templates_C). 
The components from NMF were manually categorised based on pre-knowledge of the crystal structures, orientation relationships and diffraction patterns of the precipitates. 
The categorised loading maps were thresholded before the 10\% most intense pixels in each map were taken to define region masks in real space. 
If signals from one category were split into several components, the respective loading maps could be summed prior to thresholding, or alternatively, region masks could be summed to yield one distinct region mask per category. 
Within each region, patterns were extracted from the pre-processed dataset and averaged to yield template patterns. 
This means that the NMF results were not used directly; NMF was rather used to guide the choice of distinct regions, and the template patterns were extracted from the pre-processed SPED dataset itself. 
For this reason, neither the number of components chosen for NMF, nor the thresholding of loadings, need to be optimised within this workflow. 
This stands in contrast to previous work [@Sunde2018; @Thronsen2024] and provides large benefits. 

:::{figure} ./figures/template_selections_C.png 
:name: fig_templates_C
Illustration of defining template patterns by approach (C) NMF-guided selection. The dataset is masked to reduce the data size and complexity, before NMF expresses the dataset as a combination of factors and loadings. The number of components for NMF is selected manually, and the resulting factors and loadings are categorised manually based on pre-knowledge. The loadings that correspond to unique categories are thresholded to obtain region masks. The template patterns, shown to the right, are obtained by averaging the pre-processed dataset over each region. 
:::

# Overlap templates
For the model system, it was observed that some precipitates frequently overlapped in projection. 
To accommodate for this, overlap patterns were created by simply taking the average of each pair of dissimilar template patterns and rescaling the intensity. 
These overlap templates then correspond to two phases and/or orientations and could be included in the template bank in the same manner as for the single crystal template patterns. 
This option is included in the advanced notebook (2B) on GitHub [@PMgithub], to demonstrate the flexibility of the methodology. 
Overlap patterns are not included when comparing to the ground truth. 