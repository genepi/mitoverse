# Mutserve

Mutserve is a variant caller for the mitochondrial genome to detect homoplasmic and heteroplasmic sites in sequence data. It is used by [haplocheck](../haplocheck/haplocheck.md) and [mtDNA-Server](../mtdna-server/mtdna-server.md).

## Quick Start
Mutserve requires sorted and indexed CRAM/BAM files as an input.

```
curl -sL mutserve.vercel.app | bash
./mutserve
```

## Available Tools
Currently two tools are available. 

* [call](#mutserve-call) calls homoplasmic and heteroplasmic positions. 
* [annotate](#mutserve-annotate) annotates the mutserve variant file (generated with `mutserve call`). 

## <a name="mutserve-call">Mutserve Call</a>

```
wget https://github.com/seppinho/mutserve/raw/master/test-data/mtdna/bam/input/HG00096.mapped.ILLUMINA.bwa.GBR.low_coverage.20101123.bam
curl -sL mutserve.vercel.app | bash
./mutserve call --reference rCRS.fasta --output HG00096.vcf.gz --threads 4 *.bam 
```

Please use [this reference file](https://raw.githubusercontent.com/seppinho/mutserve/master/files/rCRS.fasta) when using BAQ (disabled by default since v2.0.0).



## <a name="mutserve-annotate">Mutserve Annotate</a>

Mutserve allows to annotate the variant file (.txt) with a predefined [annotation file](https://raw.githubusercontent.com/seppinho/mutserve/master/files/rCRS_annotation_2020-08-20.txt) 

```
./mutserve annotate --input variantfile.txt --annotation rCRS_annotation_2020-08-20.txt --output AnnotatedVariants.txt
```


## Parameters

| Parameter        | Default Value / Comment          | Command Line Option | 
| ------------- |:-------------:| :-------------:| 
| Input Files     | sorted and indexed BAM/CRAM files | |
| Output Name   | output file; supported: \*.txt, \*.vcf, \*vcf.gz | `--output` |
| Reference  | reference file | `--reference` |
| Threads     | 1 | `--threads`|
| Minimum Heteroplasmy Level     | 0.01 | `--level`|
| Define specific mtDNA contig in whole-genome file     | null | `--contig-name`|
| Output Fasta     | false | `--writeFasta`|
| Output Raw File     | false | `--writeRaw`|
| MappingQuality     | 20 | `--mapQ`|
| BaseQuality     | 20 | `--baseQ`|
| AlignmentQuality     | 30 | `--alignQ`|
| Enable Base Alignment Quality (BAQ)     | false | `--baq`|
| Disale 1000 Genomes Frequence File     | false | `--noFreq`|
| Call deletions (beta)     | false | `--deletions`|
| Call insertions (beta)     | false | `--insertions`|
| Disable ANSI output     |  | `--no-ansi`|
| Show version     |  | `--version`|
| Show help     |  | `--help`|

## Output Formats

### Tab delimited File
By default (`--output filename` does not end with .vcf or .vcf.gz) we export a TAB-delimited file including *ID, Position, Reference, Variant & VariantLevel*. Please note that the *VariantLevel* always reports the non-reference variant level. The output file also includes the **most** and **second most base** at a specific position (MajorBase + MajorLevel, MinorBase+MinorLevel). The reported variant can be the major or the minor component. The last column includes the type of the variant (1: Homoplasmy, 2: Heteroplasmy or Low-Level Variant, 3: Low-Level Deletion, 4: Deletion, 5: Insertion). See [here](https://raw.githubusercontent.com/seppinho/mutation-server/master/test-data/results/variantsLocal1000G) for an example. 

### VCF
If you want a **VCF** file as an output, please specify `--output filename.vcf.gz`. Heteroplasmies are coded as 1/0 genotypes, the heteroplasmy level is included in the FORMAT using the **AF** attribute (allele frequency) of the first non-reference allele. Please note that indels are currently not included in the VCF.  This VCF file can be used as an input for https://github.com/seppinho/haplogrep-cmd.

### BAM Preperation
Mutserve is currently not focused on indel calling. 
Best Practice Pipelines include steps for BAM files preperation like local realignment around indels (*GenomeAnalysisTK.jar -T RealignerTargetCreator*, *java -jar GenomeAnalysisTK.jar -T IndelRealigner*) or BQSR (*GenomeAnalysisTK.jar -T BaseRecalibrator*).
Please also have a look at the [Mutect2 Pipeline](https://gnomad.broadinstitute.org/blog/2020-11-gnomad-v3-1-mitochondrial-dna-variants/).

## mtDNA-Server v1

The previous version of mutserve has been integrated in [mtDNA-Server v1](https://mtdna-server.uibk.ac.at).

The new changes includes the following changes: 
- mutserve always reports the non-reference level as the heteroplasmy level, while mtDNA-Server reports the minor component.
- mutserve includes a Bayesian model for homoplasmy detection. It uses the 1000G Phase 3 data as a prior and calculates the most likely posterior probability for each genotype. mtDNA-Server only outputs homoplasmic variants with a coverage > 30.