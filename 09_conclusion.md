---
title: Conclusion
---

PM is introduced as a semi-automatic data analysis method for phase mapping of SPED datasets. 
The workflow includes an effective pre-processing routine that enhances Bragg disks and greatly reduces data size. 
PM labels diffraction patterns by comparing them either to simulated template patterns or template patterns extracted from the dataset itself, using NCC as metric. 
The extracted template patterns can be manually selected or chosen based on machine learning algorithms like NMF. 

The PM method is benchmarked by mapping the spatial distribution of nano-sized precipitates in a thoroughly characterised Al-Cu-Li model alloy SPED dataset. 
Comparison to ground truth demonstrates an accuracy ${\gt}$98.5\%, regardless of whether simulated or experimental patterns are used as templates. 
Key advantages of the PM method are that poorly matching patterns can be easily identified, and that the library of templates can be updated during analysis. 
This enables both pre-known and previously unfamiliar phases to be identified and mapped. 

The PM workflow is further tested on a more challenging SPED dataset from an Al-Mg-Si-Cu alloy. 
This alloy contains precipitate phases that are partially disordered, some highly similar phases that should be distinguished, and several hybrid precipitates composed of multiple phases. 
The results are assessed for specific precipitates by comparing the phase labelling achieved by PM to manual labelling performed on atomically-resolved HAADF-STEM images, and a strong agreement is seen. 


By exploiting the advantage of updating the template bank, PM can be used to successfully map the spatial distribution of phases in more challenging cases like Al-Mg-Si-Cu alloys. 
The workflow is available open-source and can easily be adjusted and expanded to fit other material systems and challenges. 
