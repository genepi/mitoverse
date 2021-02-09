# mtDNA-Server

mtDNA-Server provides a free service for the analysis of human mitochondrial DNA data, currently focusing on reliable identification of heteroplasmy (>= 1%) and contamination. We also provide post-processing guidelines that should be applied after each automated analysis. If you want to learn about the method used behind mtDNA-Server click [here](../mutserve/mutserve.md).

## Availability
[Run a job](https://mitoverse.i-med.ac.at/) using our cloud web service.

       
## mtDNA-Server v1
The previous version of mutserve has been integrated into [mtDNA-Server v1](https://mtdna-server.uibk.ac.at).

The new version running on mitoverse includes the following changes: 
- mutserve always reports the non-reference level as the heteroplasmy level, while mtDNA-Server reports the minor component.
- mutserve includes a Bayesian model for homoplasmy detection. It uses the 1000G Phase 3 data as a prior and calculates the most likely posterior probability for each genotype. mtDNA-Server only outputs homoplasmic variants with a coverage > 30.

## How to cite

Weissensteiner Hansi, Lukas Forer, Christian Fuchsberger, Bernd Schöpf, Anita Kloss-Brandstätter, Günther Specht, Florian Kronenberg, and Sebastian Schönherr.
mtDNA-Server: Next-Generation Sequencing Data Analysis of Human Mitochondrial DNA in the Cloud. Nucleic Acids Research: gkw247. doi:10.1093/nar/gkw247. 2016
http://nar.oxfordjournals.org/lookup/doi/10.1093/nar/gkw247.