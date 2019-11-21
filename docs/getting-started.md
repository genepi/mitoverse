
## Getting Started

To calculate the contamination levels for each sample, two options are available. Here, the 1000G Phase 3 file (n=2,504) is checked for contamination. 


#### Run Haplocheck on the command line 

        mkdir haplocheck 
        cd haplocheck
        curl -s install.cloudgene.io | bash
        wget https://github.com/genepi/haplocheck/raw/master/test-data/contamination/1000G/all/1000g-nobaq.vcf.gz
        ./cloudgene install https://github.com/genepi/haplocheck/releases/download/v1.0.7/haplocheck.zip
        ./cloudgene run haplocheck@1.0.7 --files 1000g-nobaq.vcf.gz --output results
        firefox results/report/report.html
        
#### Run Haplocheck as a web service

- [Download](https://github.com/genepi/haplocheck/raw/master/test-data/contamination/1000G/all/1000g-nobaq.vcf.gz) the pre-computed 1000G VCF file.  
- Go to [mitoverse](https://mitoverse.i-med.ac.at) and login or sign-up for a new account.
- Select the haplocheck workflow and upload the variant file.
- After ~ 2 minutes all results are available for download. 