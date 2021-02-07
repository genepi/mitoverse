# mtDNA-Server

mtDNA-Server provides a free service for the analysis of human mitochondrial DNA data, currently focusing on reliable identification of heteroplasmy (>= 1%) and contamination. We also provide post-processing guidelines that should be applied after each automated analysis. A local version is available here. Follow us on Twitter for latest updates.

To calculate the contamination levels for each sample, two options are available. Here, the 1000G Phase 3 file (n=2,504) is checked for contamination. 

       
### Run mtDNA-Server as a web service

- [Download](https://github.com/genepi/haplocheck/raw/master/test-data/contamination/1000G/all/1000g-nobaq.vcf.gz) the pre-computed 1000G VCF file.  
- Go to [mitoverse](https://mitoverse.i-med.ac.at) and login or sign-up for a new account.
- Select the mtDNA-Server workflow and upload a BAM or CRAM file.
- Mitoverse sends an email as soon as the job is finished. 


## How to cite

Weissensteiner Hansi, Lukas Forer, Christian Fuchsberger, Bernd Schöpf, Anita Kloss-Brandstätter, Günther Specht, Florian Kronenberg, and Sebastian Schönherr.
mtDNA-Server: Next-Generation Sequencing Data Analysis of Human Mitochondrial DNA in the Cloud. Nucleic Acids Research: gkw247. doi:10.1093/nar/gkw247. 2016
http://nar.oxfordjournals.org/lookup/doi/10.1093/nar/gkw247.