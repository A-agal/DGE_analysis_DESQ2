---
title: "DGE Analysis Homework"

---

# Using DESeq2 for gene-level differential expression analysis

- The metadata below describes an RNA-seq analysis experiment, in which the metadata table below and associated count matrix have been loaded into R as `meta` and `counts`, respectively. Additionally, all of the appropriate libraries have been loaded for you. Use the information in the table to answer the following questions.  

	**meta**
	
	| |Genotype	|Celltype	|Batch|
	| ------ | ------- | -------- | --- |
	|sample1	|Wt	|typeA	|second |
	|sample2	|Wt	|typeA	|second|
	|sample3	|Wt	|typeA	|first|
	|sample4	|KO	|typeA	|first|
	|sample5	|KO	|typeA	|first|
	|sample6	|KO	|typeA	|second|
	|sample7	|Wt	|typeB	|second|
	|sample8	|Wt	|typeB	|first|
	|sample9	|Wt	|typeB	|second|
	|sample10	|KO	|typeB	|first|
	|sample11	|KO	|typeB	|first|
	|sample12	|KO	|typeB	|second|


	**NOTE: This is an exercise in thinking about running DESeq2. You will need to submit a functioning code that answers the following exercises.  Refer to the materials/lessons from class to answer the following questions.**

	**a.** Reorder the columns of the `counts` dataset such that `rownames(meta) == colnames(counts)`.
	
	**b.** Provide the line of code used to create a DESeqDataSet object called `dds` in which `Genotype` is the factor of interest and `Celltype` and `Batch` are other contributing sources of variation in your data.

	**c.** Provide the line of code required to run DESeq2 on `dds`.

	**d.** Provide the line of code to create a dispersion plot.

	**e.** Provide the line of code to return the results of a Wald test comparison for `Celltype` categories `typeA` versus `typeB` (i.e the fold changes reported should reflect gene expression changes relative to `typeB`).
	 
	**f.** Provide the line of code to return the results with log2 fold change shrinkage performed.

	**g.** Provide the line of code to write the results of the Wald test with shrunken log2 fold changes to file.

	**h.** Provide the line of code to subset the results to return those genes with adjusted p-value < 0.05 and logFold2Change > 1.

# Working with the DESeq2 results table

- Using the de_script.R that we created in class for the differential expression analysis, change the thresholds for adjusted p-value and log2 fold change to the following values:
 
	```r
	padj.cutoff <- 0.01
	
	lfc.cutoff <- 1.5
	```
	
	Using these new cutoffs, perform the following steps:

	**a.** Subset `res_tableOE` to only return those rows that meet the criteria we specified above (adjusted p-values < 0.01 and log fold changes >1.5). Save the subsetted table to a data frame called `sig_table_hw_oe`. Write the code below:

	**b.** There is a a DESeq2 function that summarizes how many genes are up- and down-regulated using our criteria for `alpha=0.01`. Use this on the `sig_table_hw_oe`. Write the code you would use, and also, list how many genes are up- and down- regulated.

	**c.** Get the gene names from `sig_table_hw_oe` and save them to a vector called `sigOE_hw`. Write the code below:

	**d.** Write the `sigOE_hw` vector of gene names to a file called `sigOE_hw.txt` using the `write()` function. Ensure the genes are listed in a single column. Write the code below.
	 
# Visualizing Results

- For the genes that are differentially expressed in the knockdown versus control comparison (`res_tableKD`), plot an expression heatmap using normalized counts and `pheatmap()` following the instructions below. Write the code you would use to create the heatmap.

	**a.** The heatmap should only include control and knockdown samples. 

	**b.** Set up a heat.colors vector using a palette of your choice from brewer.pal (make sure it is different from the one used in class).

	**c.** Plot the heatmap without clustering the columns. 

	**d.** Scale expression values by row.

# Use significant gene lists to find overlaps between the two comparisons 

- Using the original cutoff values, perform the following steps:

	```r
	padj.cutoff < 0.05

	lfc.cutoff > 0.58
	```
	
	**a.** Create separate vectors with gene names for up-regulated genes and down-regulated genes from `res_tableOE` and save as `up_OE` and `down_OE`, respectively. Write the code below:

	**b.** Create separate vectors with gene names for up-regulated genes and down-regulated genes from `res_tableKD` and save as `up_KD` and `down_KD`, respectively. Write the code below:

	**c.** Test for overlaps between the lists:
	
	- How many, and which genes in `up_OE` are also in `down_KD`?
	
	- How many, and which genes in `up_KD` are also in `down_OE`?
	
 
