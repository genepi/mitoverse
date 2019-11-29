# FAQ

**What is the difference b/w overall homo/heteroplasmies and amount major/minor homo/heteroplasmies?**  

Overall homoplasmies/heteroplasmies count the number of variants found in a sample. E.g. sample A includes 10 homoplasmies and 8 heteroplasmies. Haplocheck splits the variants into two profiles, a major profile and a minor profile. The major profile includes all homoplasmies and the major part of the heteroplasmy. The minor profile includes all hoomoplasmies and the minor part of the heteroplasmy. For each profile, the haplogroup is calculated using Haplogrep. Ideally, all variants are used and a quality score of 1 is reached. For lower quality scores, some homoplasmies/heteroplasmies could not be found for the best hit. The columns "Major/minor homoplasmies/heteroplasmies" count the number of variants that have been used for the best haplogroup hit.    

**What does the heteroplasmy level represent?**

The heteroplasmy level denotes the averaged allele frequency (VAF) and is calculated for both the major (column `Major Heteroplasmy Level`) and minor (column `Minor Heteroplasmy Level`) profile.

**How is the heteroplasmy level calculated?**

The major and minor heteroplasmy level is calculated by using only heteroplasmies from the most previous common ancestor of both components. For example, if **H1a1** is the common ancestor of the profiles H1a1a1 (major) and H1a1b (minor), only heteroplasmies starting from H1a1 are counted. Furthermore, we only count heteroplasmies with a mutation rate > 5 (as defined by HaploGrep) and excluding back mutations as well as deletions on heteroplasmies. Each heteroplasmy is split in a major and minor part to calculate the level for both profiles.

**How is the label contamination (YES versus NO) decided exactly?**

Haplocheck uses the mitochondrial phylogeny and the concept of haplogroups to identify contamination. It is heavily based on [Haplogrep](https://github.com/seppinho/haplogrep-cmd) and [Mutserve](https://github.com/seppinho/mutserve). Mutserve allows to detect low-level variants (or in case of mtDNA so called **heteroplasmies**) down to the variant level of 1 %. Haplocheck splits the input into two profiles and calculates the haplogroup for each profile. Identical haplogroups are marked with the contamination status of **NO**. If the haplogroup between the two profiles differ, high confident heteroplasmies are determined and the distance between the two profiles is calculated. Depending on the (a) amount of heteroplasmies, (b) haplogroup quality score and (c) distance between two profiles a YES label is assigned.
