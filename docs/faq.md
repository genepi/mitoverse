# FAQ

**What is the difference b/w overall homo/heteroplasmies and amount major/minor homo/heteroplasmies?**  

Overall homoplasmies/heteroplasmies count the number of variants found in a sample. E.g. sample A includes 10 homoplasmies and 8 heteroplasmies. Haplocheck splits the variants into two profiles, a major profile and a minor profile. The major profile includes all homoplasmies and the major part of the heteroplasmy. The minor profile includes all hoomoplasmies and the minor part of the heteroplasmy. For each profile, the haplogroup is calculated using Haplogrep. Ideally, all variants are used and a quality score of 1 is reached. For lower quality scores, some homoplasmies/heteroplasmies could not be found for the best hit. The columns "Major/minor homoplasmies/heteroplasmies" count the number of variants that have been used for the best haplogroup hit.    

**What does the heteroplasmy level represent?**
The heteroplasmy level denotes the averaged allele frequency (VAF) and is calculated for both the major (column `Major Heteroplasmy Level`) and minor (column `Minor Heteroplasmy Level`) profile.

**How is the heteroplasmy level calculated?**
The major and minor heteroplasmy level is calculated by using only heteroplasmies from the most previous common ancestor of both components. For example, if **H1a1** is the common ancestor of the profiles H1a1a1 (major) and H1a1b (minor), only heteroplasmies starting from H1a1 are counted. Furthermore, we only count heteroplasmies with a mutation rate > 5 (as defined by HaploGrep) and excluding back mutations as well as deletions on heteroplasmies. Each heteroplasmy is split in a major and minor part to calculate the level for both profiles. 
