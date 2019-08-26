# FAQ

!!! question
	How is the value in "MajorLevel" and "MinorLevel" calculated?  
	The major and minor level is calculated using only heteroplasmies from the most previous common ancestor of both components. For example, if **H1a1** is the 	common ancestor of the final components H1a1a1 and H1a1b, only heteroplasmies starting from H1a1 are counted. Furthermore, we only count heteroplasmies with a 	mutation rate > 5 (as defined by HaploGrep) and excluding back mutations as well as deletions on heteroplasmies.