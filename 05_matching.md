---
title: Pattern matching
numbering:
  enumerator: 4.%s
---

The major steps in the pattern matching workflow after pre-processing is schematically presented in Figure [](#fig_pm) for the model dataset. 
After defining template patterns (step 2.0), matching is performed by calculating the normalised cross-correlation (NCC) score to all the template patterns, for each pre-processed PED pattern in the SPED dataset (step 2.1). 
The NCC match score is defined as \cite{NCC}: 
\begin{align}
    \frac{\sum_{k_x,k_y}\left[I_{\text{p}}(k_x,k_y)-\overline{I_{\text{p}}}\right]\left[I_{\text{t}}(k_x,k_y)-\overline{I_{\text{t}}}\right]}{\sqrt{\sum_{k_x,k_y}\left[I_{\text{p}}(k_x,k_y)-\overline{I_{\text{p}}}\right]^2\sum_{k_x,k_y}\left[I_{\text{t}}(k_x,k_y)-\overline{I_{\text{t}}}\right]^2}},
\end{align}
where $I_\text{p}(k_x,k_y)$ and $I_\text{t}(k_x,k_y)$ are the intensities of a pre-processed PED pattern and a template pattern, respectively, and $\overline{I_\text{p}}$ and $\overline{I_\text{t}}$ are their respective average intensities. 
Only intensities included within a signal mask are included in this NCC calculation. 
The signal mask blocks out the direct beam region, the Al Bragg disks and higher scattering angles, so that these regions are not considered. 

:::{figure} 
:name: fig_pm
:placeholder: ./figures/pm.png
Schematic workflow of pattern matching: (2.0) Define template patterns, (2.1) match each pattern with all the templates within a signal-masked region, (2.2) label patterns according to the match scores, and (2.3) identify unlabelled patterns that can be used as basis for defining new templates.
:::

After calculating the match scores, the patterns are labelled to produce a phase map (step 2.2). 
This is normally done by assigning the phase corresponding to the highest NCC score. 
Phase labelling was also done using the same prioritisation scheme as in the previous work [@Thronsen2024], to ensure a fair comparison between the model system phase map and the ground truth. 
For comparison, the phase mapping accuracy was defined as the percentage of patterns for which the phase labelling in the resulting phase map was identical to that in the ground truth. 

The map of the highest NCC scores per probe position is inspected to identify low maximum NCC scores and thereby patterns that do not resemble any of the template patterns to a sufficient degree. 
The NCC score map is thresholded to reveal the lowest NCC scores, and additional templates can then be searched for within these low match score regions (step 2.3). 
This option is included in the advanced notebook for the model system which presents two ways of finding additional templates; NMF (as explained earlier) and a density-based clustering algorithm. 

For the test system, additional templates were sought after using NMF. 
To capture all of the unique pattern types, the cycle of matching and searching for additional templates was repeted three times. 
In addition, since the L phase patterns closely resemble those from the C phase, the patterns initially labelled as L or C were manually re-inspected to verify correct labelling. 
If L or C patterns had been mislabelled as C or L respectively, that C or L pattern was added to the template bank before the matching was redone and the phase map updated. 
