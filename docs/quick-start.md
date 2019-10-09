
## Quick Start

To run the 1000 Genomes Phase 3 VCF file  with haplocheck, the following steps are required:


### Run 1000G VCF Locally 

        curl -s install.cloudgene.io | bash -s 2.0.0-rc14
        wget https://github.com/genepi/haplocheck/raw/master/test-data/contamination/1000G/all/1000g-nobaq.vcf.gz
        ./cloudgene install https://github.com/genepi/haplocheck/releases/download/v1.0.5/haplocheck.zip
        ./cloudgene run haplocheck@1.0.5 --files 1000g-nobaq.vcf.gz --output 1000g-out
        
### Run 1000G on the mitoverse Cloud Platform 


- The pre-computed VCF file can be downloaded from [here](https://github.com/genepi/haplocheck/raw/master/test-data/contamination/1000G/all/1000g-nobaq.vcf.gz)
- Go to https://mitoverse.i-med.ac.at and login/sign-up a new user account
- Select the haplocheck workflow and upload the 1000g-nobaq.vcf.gz
- After around 2 minutes the final report (report.html) is ready and all haplogroups can be analysed.