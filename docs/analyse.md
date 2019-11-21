
## Analyse Result Files 

### Graphical Report

Haplocheck reports the contamination status for each input sample and a graphical report is created.

![Result Report](img/report1.png)

#### Graphical Presentation
To check for contamination in detail, we provide for each mixture a graphical representation of the phylogenetic tree. The tree starts at the root node (rCRS) and shows homoplasmic (blue) / heteroplasmic (green) positions for each transition.

![Phylogenetic Tree](img/report_tree.png)


### Result file

Additonally, a text file including all results is created as well. The following columns are included:

- Sample: This columns includes the sample identifier. 

- Contamination Status: Haplocheck works by splitting each input sample into two profiles, the so called "major" and "minor" component. Homoplasmies are always added to both profiles, heteroplasmies are split and added to the correct profile. This column can either be "YES" or "NO". 

- Overall Homoplasmies: Amount of detected homoplasmies in the sample.

- Overall Heteroplasmies: Amount of detected heteroplasmies in the sample.

- Sample Coverage: Sample coverage

- Major Haplogroup: Input profile is classified by using Haplogrep. The input profile includes all homoplasmies and the major component of each heteroplasmy

- Major Haplogroup Quality: This columns includes the haplogroup quality (provided by Haplogrep). See [here](http://haplogrep.uibk.ac.at/blog/explaining-the-formula/) for details.

- Minor Haplogroup: Input profile is classified by using Haplogrep. The input profile includes all homoplasmies and the major component of each heteroplasmy

- Minor Haplogroup Quality: This columns includes the haplogroup quality score (provided by Haplogrep). See [here](http://haplogrep.uibk.ac.at/blog/explaining-the-formula/) for details.

- Amount Major Homoplasmies: Amount of homoplasmies used for the major haplgroup. Please keep in mind that Haplogrep assigned the best haplogroup hit and traverses through the graph. 

- Amount Minor Homoplasmies: Amount of homoplasmies used for the minor haplgroup. 

- Amount Major Heteroplasmies: Amount of heteroplasmies used for the major haplgroup. lease keep in mind that Haplogrep assigned the best haplogroup hit and traverses through the graph. 

- Amount Minor Heteroplasmies: Amount of heteroplasmies used for the minor haplgroup. 

- Major Heteroplasmy Level: The major heteroplasmy level is calculated by averaging the level of the major component of each heteroplasmy. Only heteroplasmies from the common ancestor of the major and minor profile are used. Figure 1 shows the phylogenetic graph of sample HG00245. H is the common ancestor for both components, therefore only heteroplasmies 6776C (0.985), 10754C (0.981), 3992T (0.985), 4418C (0.98) and 8950A (0.989) are used for the level calculation. By averaging all levels, a final major level of 0.984 is calculated. 

![Figure1](img/heteroplasmy_major.jpg)

- Minor Heteroplasmy Level: The minor heteroplasmy level is calculated by averaging the level of the minor component of each heteroplasmy. For sample HG00245 only the minor compoment of 3010A (0.011) and 16356C (0.012) is used resulting in a final heteroplasmy level of 0.011. 

- Distance: This column defines the distance between the haplogroups of the major and minor profile using the graph structure of Phylotree 17. 

- Clusters: All heteroplasmies are clustered using the Jenks natural breaks classification method. This information is provided to the user, to see if different clusters can be identified by haplocheck. 

