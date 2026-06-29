---
title: The model system
numbering:
  enumerator: 6.%s
---

[](#fig_priority) presents an interactive figure where the six phase maps resulting from using the three ways of defining templates (A: simulations; B: manual; C: NMF) and two ways of phase labelling (maximum NCC; prioritisation scheme), each can be displayed next to the ground truth phase map. 
A difference map is also presented that shows correspondence to ground truth in black and any discrepancies in white. 
The main difference between the two phase labelling strategies is whether the $\theta$'$_{\langle001\rangle}$ plates (blue) that give only a few weak Bragg disks are prioritised over overlapping T$_{1}$ segments (green). 
Mislabelling at or near phase interfaces is a common feature in all the phase maps, due to weak precipitate Bragg disks, and/or interface effects and strain. 
The same was reported in the previous study [@Thronsen2024], where it was also pointed out that such artefacts are relatively harmless unless precipitate size statistics is to be extracted from the phase maps. 
The accuracies of the phase maps relative to the ground truth are summarised in [](#table3). 
All yield accuracies ${\gt}$98.5\%, demonstrating strong agreement between the derived phase maps, the ground truth, and the previously presented results [@Thronsen2024]. 

:::{figure} #app:ground_truth_comparison_widget
:name: fig_priority
:placeholder: ./figures/ground_truth_placeholder.png
Al-Cu-Li alloy ground truth phase map displayed next to a phase map made by PM. The difference between the two is shown below. Template patterns are either (A) kinematically simulated, (B) averaged from manually selected regions in the dataset, or (C) averaged from the dataset according to NMF results. The phase labelling scheme is either based on maximum NCC score or according to the phase priority: (1) $\theta'_{\langle100\rangle}$, (2) T$_{1}$, and (3) $\theta'_{\langle001\rangle}$.
:::

```{list-table} Phase mapping accuracy for three different approaches (A-C) of defining template patterns for the Al-Cu-Li model system dataset. The accuracy is obtained by comparing to ground truth and is reported for two labelling schemes: highest NCC score and phase priority. 
:header-rows: 2
:name: table3
* - Template type
  - Accuracy (\%) 
* - 
  - max NCC
  - priority
* - (A) Simulations
  - 98.65 
  - 98.72
* - (B) Manual selection
  - 98.84
  - 98.95
* - (C) NMF-guided selection
  - 98.90
  - 98.99
```

To examine some of the mislabelled regions in more detail, the phase map produced by using approach (A) simulated templates is used, since this one has the most discrepancies. 
The phase map and difference map are shown in [](#fig_sim)(a) and (b), respectively, where two regions with mislabelled $\theta$'$_{\langle100\rangle}$ precipitates (orange) and a third region containing a mislabelled T$_{1}$ segment (green), are highlighted.
These three areas are magnified and overlayed with the difference map in [](#fig_sim)(c)-(e). 
One correctly labelled and one incorrectly labelled single pre-processed PED pattern are presented under each region in (c)-(e). 
These patterns are overlayed with dashed circles that represent the Bragg spots of the simulated templates that would be correct according to the ground truth phase map. 
For (c) and (d), the mislabelled regions correspond to bent $\theta$'$_{\langle100\rangle}$ precipitates, and the corresponding patterns show weaker and less Bragg spots compared to the correctly labelled patterns. 
The mislabelled segment inside the T$_{1}$ precipitate, shown in [](#fig_sim)(e), is a common feature in all the phase maps. 
The selected PED patterns in (e) are overlayed with the simulated Bragg spots corresponding to the template of T$_{1-2}$, which is expected based on the ground truth. 
The pattern in the mislabelled region does not, however, appear similar to this simulated pattern, and the pattern represents a new unique diffraction pattern that was not included in the original template bank. 

:::{figure} ./figures/pm_sim.png
:name: fig_sim
PM of the model dataset with simulated templates (A). (a) Phase map, and (b) difference map with respect to the ground truth. Three regions are highlighted where precipitate segments are incorrectly labelled according to the ground truth. (c)-(e) Zoomed-in maps from the highlighted regions with single PED patterns from indicated regions included underneath. The patterns are pre-processed until step 1.2 (left) and 1.4 (right). The patterns in (c) and (d) are overlayed with dashed circles that represent the disk positions in the two $\theta$'$_{\langle100\rangle}$ templates that are correct based on the ground truth. The diffraction patterns in (e) are overlayed with dashed circles showing the disk positions in templates from the expected T$_{1}$ phase. All PED patterns are plotted in log-scale, and overlayed with stars representing the centre spot (red) and the Al reflections (white).
:::

One of the main advantages of the PM workflow is that additional templates can easily be included after the first phase mapping step. 
To demonstrate this possibility, additional template patterns were searched for in regions with low NCC scores and added to the template bank. 
Furthermore, template patterns representing pairs of overlapping crystals were also defined and included in the template bank to further highlight the flexibility of the PM approach. 
[](#fig_advanced) presents an interactive plot where the user can choose between four types of template banks and inspect the resulting maximum NCC score map and phase map. 
The first template bank option ('NMF') only comprises the original templates found via the first round of NMF-based template selection, while the second option ('NMF + overlap') also contains the corresponding overlap patterns made by summing pairs of these original template patterns. 
The third and fourth option include additional templates found by searching for new templates in regions with low maximum NCC scores using NMF-guided selection ('NMF + overlap + NMF') or clustering-based selection ('NMF + overlap + clustering'). 
The latter two phase maps therefore contain new labels, which correspond to the bent $\theta$'$_{\langle100\rangle}$ segments discussed in the previous paragraph. 
The missing unfamiliar T$_{1}$ segment highlighted in [](#fig_sim)(e) is also incorporated and labelled 'x'. 
These updated phase maps thus demonstrate that both pre-known and unfamiliar patterns can be identified and mapped after an additional iteration of searching for new templates. 
Moreover, overlapping crystals can be correctly labelled along with non-overlapping crystals, which suggests that the previously used phase prioritisation scheme [@Thronsen2024] becomes unnecessary. 

:::{figure} #app:advanced_phase_map_widget
:name: fig_advanced  
:placeholder: ./figures/advanced_placeholder.png
Maximum NCC score map and phase map for the Al-Cu-Li model alloy dataset for a user-selected type of template bank. Based on the template bank, the phase map may show both single and pairs of overlapping precipitate phases ('+'), bent precipitate segments ($_{-1/2-2/3}$), and an unfamiliar category ('x'). 
:::