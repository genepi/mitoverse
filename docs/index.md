# Haplocheck

Haplocheck is a contamination detection tool using the mtDNA phylogeny. You can upload alignment files (BAM,CRAM) or variant files (vcf, vcf.gz) and receive a graphical and textual report which can be shared with collaborators. 

We provide haplocheck as a [standalone pipeline](https://github.com/genepi/haplocheck#run-haplocheck-locally) and as a cloud web service (via https://mitoverse.i-med.ac.at).

## Haplocheck Workflow
Currently the workflow includes the following steps:

* Variant and Heteroplasmy Detection using [mutserve](https://github.com/seppinho/mutserve)
* Haplogroup Detection using [HaploGrep](https://github.com/seppinho/haplogrep-cmd)
* Contamination Detection
* Graphical Report Creation

Haplocheck is already available in mitoverse. Please click [here](https://mitoverse.i-med.ac.at/index.html#!run/haplocheck%401.0.5) to run your first contamination check.