
## Getting Started

To calculate the contamination levels for each sample, two options are available. In both cases the 1000G Phase 3 file (n=2504) is analyzed. 


#### Run haplocheck locally 

        mkdir haplocheck 
        cd haplocheck
        curl -s install.cloudgene.io | bash
        wget https://github.com/genepi/haplocheck/raw/master/test-data/contamination/1000G/all/1000g-nobaq.vcf.gz
        ./cloudgene install https://github.com/genepi/haplocheck/releases/download/v1.0.6/haplocheck.zip
        ./cloudgene run haplocheck@1.0.6 --files 1000g-nobaq.vcf.gz --output results
        firefox results/report/report.html
        
#### Run haplocheck using the mitoverse cloud platform 

- [Download](https://github.com/genepi/haplocheck/raw/master/test-data/contamination/1000G/all/1000g-nobaq.vcf.gz) the pre-computed VCF file  
- Go to [mitoverse](https://mitoverse.i-med.ac.at) and login or sign-up for a new account
- Select the haplocheck workflow and upload the variant file
- After around 2 minutes the final report (report.html) is ready and all results are available for download. 