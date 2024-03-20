# mtDNA-Server 2

mtDNA-Server 2 provides a free service for the analysis of human mitochondrial DNA data, currently focusing on reliable identification of heteroplasmy (>= 1%) and contamination. We also provide post-processing guidelines that should be applied after each automated analysis.

## Availability
[Run a job](https://mitoverse.i-med.ac.at) using our cloud web service or checkout the source code on [GitHub](https://github.com/genepi/mtdna-server-2).

## Workflow 
First, users upload BAM files and an Input Validation step is executed. For all samples, which are passing Input Validation, a FastQC report is created, summarized with MultiQC. Next, one of the available variant callers (mutserve or Mutect2) can be selected. Detected variants are annotated and a contamination check as well as a haplogroup assignment process are executed (using the previously published haplocheck and haplogrep3 tools from our institute). All created files are finally summarized in an interactive HTML report. 

![Overall Architecture](images/overall.png)


### Registration
The sign-up process on mitoverse is straight-forward. After accessing the landing page, click on "Sign up". Mitoverse allows to register **with or without an email**. In case no email is specified, mitoverse does not send a job status email.

![Sign up](images/signup.png)

### Job Submission
After sign-up is completed, user are able to submit new jobs. Users can submit BAM files and specify numerous parameters:

#### Input Files
The "Input Files" field enables you to select one or multiple mtDNA aligned reads in BAM Format. These files contain the genetic information necessary for the analysis performed by the mtDNA-Server 2.

#### Mode
In the "Mode" field, you can select the mode for analysis. Options include fusion, mutect2, and mutserve. Choosing the appropriate mode ensures that the analysis is tailored to your specific requirements.

#### Detection Limit
The "Detection Limit" field allows you to select the detection limit for the analysis. This parameter determines the sensitivity of the analysis to detect mutations or variations in the input data.

#### Apply Coverage Estimate
With the "Apply Coverage Estimate" field, you can choose whether to apply coverage estimation. This option helps in assessing the depth and uniformity of coverage across the input data, aiding in the accuracy of the analysis results.

#### Coverage Subsampling
Specify the desired mean coverage by entering the number of coverage you want to use. mtDNA-Server 2 automatically subsamples the uploaded reads to achieve this mean coverage. Enter "0" to deactivate coverage subsampling.

#### Minimal Base Quality
In the "Minimal Base Quality" field, specify the minimal base quality required for analysis. This parameter ensures that only high-quality bases are considered during the analysis process, improving the reliability of the results.

#### Minimal Map Quality
The "Minimal Map Quality" field allows you to specify the minimal map quality required for analysis. This parameter helps filter out reads with poor mapping quality, ensuring that only accurately mapped reads contribute to the analysis.
        |

![Submit a job](images/submit.png)



### Job Monitoring
Mitoverse returns constant feedback to the users about the current job status (waiting, running, finished) and also return details about each job step. 

![Submit a job](images/run.png)

### Job Results

All results are available in the Results tab. This currently includes a QC-report, the annotated variants, haplogroup and sample information as well as an interactive report (report.html).

![Results](images/results.png)


#### Report
After the job has been finished, users can download the interactive report to explore the data in detail which can also be easily shared with collaborators without a login.

![Report](images/report.png)

By clicking on a sample name, a new tab opens with more details of the sample and all detected variants and heteroplasmies:

![Report-Details](images/report-details.png)


#### Variants
The "Variants" section includes files related to variant analysis.

the file **variants.annotated.txt** contains detailed information about the detected variants, including annotations. It is a tab delimted file and has the following columns:

| Column                 | Description                                                                                     |
|------------------------|-------------------------------------------------------------------------------------------------|
| Mutation               | Defines variant with POS and ALT allele                                                        |
| POS                    | Position of the variant according to the rCRS, see [rCRS_annotated](https://phylotree.org/resources/rCRS_annotated.htm) |
| REF                    | Reference allele of the rCRS, see also [rCRS_annotated](https://phylotree.org/resources/rCRS_annotated.htm) |
| ALT                    | Alternative allele observed on the current position                                              |
| Substitution           | Type of Substitution: Transition (A>G, G>A, T>C, C>T) or transversion (other)                   |
| Maplocus               | 40 different loci, including 2 MT-DLOOP(1,2), 2 MT-RNR1(2), 13 genes MT-ATP6 -> MT-ND6, 22 tRNA and noncoding (empty) |
| Category               | 5 different categories: tRNA, rRNA, Coding, Control Region and “-” (noncoding)                 |
| Phylotree17_haplogroups| How many haplogroups in phylotree 17 have a variant                                             |
| Phylotree17_clades     | How many different occurrences (fluctuation rate) in different clades can be observed            |
| HaploGrep2_weight      | Weight based on the log-transformed value on the Phylotree17_clades. Value between 1 (highest value) and 10 (only occurring in 1 clade) |
| RSRS_SNP               | Is this SNP a RSRS defining SNP, see [RSRS_vs_rCRS](https://phylotree.org/resources/RSRS_vs_rCRS.htm) 1=yes, 0=no |
| KGP3_SNP               | Was this SNP observed in the 1000 Genomes Project Phase 3 (low-coverage) data? 1=yes, 0=no     |
| AAC                    | Amino Acid Change, denoted with the short Amino Acid Symbol, position on protein and the new amino acid change, e.g. M1L |
| CodonPosition          | Position of the codon defining the mRNA sequence, values: 1,2,3 or NA                           |
| AminoAcid              | The amino acid encoded by the reference based codon, e.g. M for Methionine                      |
| NewAminoAcid           | The amino acid encoded by the alternative codon, e.g. L for Leucine                             |
| AminoAcid_pos_protein  | Amino acids position on the produced protein                                                   |
| MutPred_Score          | Pathogenicity Score based on MutPred – see [MutPred](https://doi.org/10.1093/bioinformatics/btp528) – values between 0 (benign) and 1 with values > 0.5 potentially deleterious |
| mtDNA_Selection_Score  | Pathogenicity Score as presented in Pereira et al, [Pereira et al](https://doi.org/10.1016/j.ajhg.2011.03.006), log-transformed MutPred score – values between 0 and ~ 3 - values > 0.5 potentially deleterious |
| CI_MitoTool	         | Conservation Index (CI) as used in MitoTool, see 10.1016/j.mito.2010.09.013 and Ruiz-Pesini et al https://www.science.org/doi/full/10.1126/science.1088434  |
| OXPHOS_complex		 | Indicates whether a variant is on a gene encoding one of the  OXPHOS complexes I, III, IV or V  |
| NuMTs_dayama	         | SNP observed in the 1000 Genomes Project Phase 1 data occuring as part of a NUMT  (Dayama et al 10.1093/nar/gku1038) ? Numbers indicating how many fragments with SNP were found  |
| Helix_count_hom	     | Homoplasmic variant count in HelixMTdb https://www.helix.com/mitochondrial-variant-database  |
| Helix_count_het	     | Heteroplasmic variant count in HelixMTdb https://www.helix.com/mitochondrial-variant-database  |
| Helix_vaf_hom	         | Variants Allele Frequency of homoplasmic variants in HelixMTdb = count / (n=~195,000)  |
| Helix_vaf_het	         | Variants Allele Frequency of heterioplasmic variants in HelixMTdb = count / (n=~195,000)  |
| Helix_haplogroups	     | Haplogroups found with the variant HelixMTdb  |
| rCRS_Surr_seq	         | Surrounding nucleotides based on the POS of the current variant on the reference sequence rCRS e.g. (CCCTC[T/A]AAATC)  |
| LowComplexityRegion	 | Checks if rCRS_Surr_seq includes homopolymeric stretches of length 4 or longer (0 = no, 1=yes)  |
| DuplSeq_rCRS	         | Is this motif (rCRS_Surr_seq) length 11bps found on a different position on the rCRS (0=no, 1=yes)  |
| DuplSeq_rCRS_pos	     | if motif is found as duplicate, coordinates of the position on the rCRS  |




#### Auxiliary Files
The "Auxiliary Files" section includes additional files generated during the analysis.

- **excluded_samples.txt**: This file lists any samples that were excluded from the analysis, along with the reason for their exclusion.
- **haplocheck.html**: The HTML report from Haplocheck provides information about contamination.
- **haplocheck.txt**: The text file containing contamination information and quality assessment results from Haplocheck.
- **haplogroups.txt**: This file contains the assigned mitochondrial haplogroups for each sample analyzed.
- **sample_mappings.txt**: The sample mappings file provides information about the mapping between sample IDs and their corresponding filenames.
- **sample_statistics.txt**: This file contains statistical summaries and metrics for each sample analyzed in the study.


## Citation

Weissensteiner Hansi, Lukas Forer, Christian Fuchsberger, Bernd Schöpf, Anita Kloss-Brandstätter, Günther Specht, Florian Kronenberg, and Sebastian Schönherr.
mtDNA-Server: Next-Generation Sequencing Data Analysis of Human Mitochondrial DNA in the Cloud. Nucleic Acids Research: gkw247. doi:10.1093/nar/gkw247. 2016
http://nar.oxfordjournals.org/lookup/doi/10.1093/nar/gkw247.
