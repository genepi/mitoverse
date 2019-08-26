
## Installation

The complete pipeline has been integrated into (Cloudgene)[https://www.cloudgene.io] for local usage and to provide it as a cloud web service. 
### Local Usage

For local usage on the command line, only Java 8 or higher is required. 

        curl -s install.cloudgene.io | bash -s 2.0.0-rc14
        ./cloudgene install https://github.com/genepi/haplocheck/releases/download/v1.0.5/haplocheck.zip
        ./cloudgene run haplocheck@1.0.5 --files <input-files> --output <folder>  
        
### Cloud Web Service
        
To use our cloud web service, please click (here)[https://mitoverse.i-med.ac.at/].