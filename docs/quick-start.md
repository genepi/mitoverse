
## Quick Start

To check the 1000 Genomes Phase 3 VCF file for contamination, two options are available:


### Run 1000G VCF locally 

        mkdir haplocheck 
        cd haplocheck
        curl -s install.cloudgene.io | bash
        wget https://github.com/genepi/haplocheck/raw/master/test-data/contamination/1000G/all/1000g-nobaq.vcf.gz
        ./cloudgene install https://github.com/genepi/haplocheck/releases/download/v1.0.6/haplocheck.zip
        ./cloudgene run haplocheck@1.0.6 --files 1000g-nobaq.vcf.gz --output results
        firefox results/report/report.html
        
### Run 1000G on the mitoverse cloud platform 


- The pre-computed VCF file can be downloaded from [here](https://github.com/genepi/haplocheck/raw/master/test-data/contamination/1000G/all/1000g-nobaq.vcf.gz)
- Go to [mitoverse](https://mitoverse.i-med.ac.at) and login or sign-up for a new account
- Select the haplocheck workflow and upload the 1000g-nobaq.vcf.gz
- After around 2 minutes the final report (report.html) is ready and all results are available for download