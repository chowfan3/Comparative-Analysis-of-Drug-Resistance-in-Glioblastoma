# Olaparib Resistance Analysis
A project by Sean Fan 08/06/25

Abstract:

Acquired resistance to chemotherapy is a major clinical challenge in treating glioblastoma. This project aimed to identify genes associated with resistance to the drug Olaparib by analyzing the public gene expression dataset GSE295766. A bioinformatics procedure was developed in Python to perform a differential expression analysis between drug-sensitive and drug-resistant cell lines. The analysis identified 263 significantly upregulated and 403 significantly downregulated genes (Log2 Fold Change > |1| and p-value < 0.05). The response was notably asymmetric, with upregulated genes showing greater magnitudes of change and higher statistical significance. Subsequent pathway enrichment analysis did not find any significant functional pathways, suggesting a complex, multi-faceted mechanism of resistance driven primarily by gene activation.

Introduction:

Glioblastoma is an aggressive form of brain cancer with poor patient outcomes that is mainly due to the development of therapeutic resistance. A standard treatment involves chemotherapy, but cancer cells often adapt and survive, rendering drugs like Olaparib ineffective. Understanding the genetic changes that allow cancer cells to overcome treatment is critical for designing more effective therapies. Here we investigated the molecular changes behind this phenomenon by analyzing a publicly available dataset (NCBI GEO: GSE295766) to answer the question: Which genes and biological pathways are associated with acquired Olaparib resistance in glioblastoma cells?

Methods:

Our analysis was conducted in a Jupyter Notebook using Python. The following procedure was executed:

Data Acquisition and Cleaning: The dataset GSE295766_All.FPKM.xls was loaded into a pandas DataFrame. All expression value (FPKM) columns were systematically cleaned by converting them to a numeric data type and replacing any non-numeric entries with zero.

Differential Expression Analysis: Replicate samples for the control (drug-sensitive) and resistant conditions were first averaged. To focus on active genes, genes with an average FPKM value of less than 1 in both conditions were filtered out.

Statistical Analysis: An independent two-sided t-test was performed for each gene to compare the control and resistant replicate groups, generating a p-value to measure statistical significance. The Log2 Fold Change (Log2FC) was calculated to measure the magnitude and direction of the expression change.

Pathway Enrichment Analysis: The list of significantly upregulated gene symbols was analyzed for functional enrichment using the gseapy Python library against the KEGG and Gene Ontology (GO) databases.

Results:

Visualization of Differential Gene Expression
The relationship between expression change (Log2 Fold Change) and statistical significance (-Log10 P-value) for all expressed genes is visualized in the volcano plot (Figure 1). The plot reveals a highly asymmetric response to drug resistance. A distinct population of 263 significantly upregulated genes (red points) is visible in the top-right quadrant. In contrast, while 403 genes were significantly downregulated (blue points), they are clustered closer to the significance thresholds, indicating that the upregulation response was more pronounced in both magnitude and statistical significance.

Figure 1: 
<img width="2960" height="2343" alt="volcano_plot" src="https://github.com/user-attachments/assets/723d1d79-9e45-438d-ae77-aa7293ae7199" />
Volcano plot visualizing gene expression changes. Red points represent genes with statistically significant upregulation, and blue points represent genes with statistically significant downregulation.

Candidate Gene Analysis:

The top 10 genes with the largest increase and decrease in expression are detailed in Table 1 and Table 2, respectively. These tables distinguish between genes with a large fold change and those that are also statistically significant.

Table 1: 
<img width="2996" height="636" alt="top_10_upregulated_genes" src="https://github.com/user-attachments/assets/3b1e7174-9115-4297-aff0-ecab546de82e" />
The top 10 most upregulated genes, ranked by Log2 Fold Change. Of this list, the top statistically significant candidate is ENSG00000123983, with a large fold change (6.58) and a strong p-value (0.02).

Table 2: 
<img width="2996" height="636" alt="top_10_downregulated_genes" src="https://github.com/user-attachments/assets/18272c49-d918-41d5-969e-d99d0d86ef72" />
Table 2: The top 10 most downregulated genes, ranked by Log2 Fold Change. The top hit, ENSG00000165507, is statistically significant with a fold change of -6.60 and a p-value of 0.03.


Pathway Analysis Results:

To understand the biological context of these changes, a pathway enrichment analysis was performed on the lists of up and down-regulated genes. This analysis against the KEGG and Gene Ontology databases returned no statistically significant pathways after correction for multiple testing.

Discussion and Conclusion
To conclude, we have successfully identified hundreds of genes whose expression is significantly altered in Olaparib-resistant glioblastoma cells. The key finding, visualized in the volcano plot, is the asymmetric nature of the genetic response. Although more genes were downregulated, the upregulated genes showed a greater average magnitude of change and higher statistical significance. This suggests that the primary mechanism for acquiring resistance in this model is the strong, active upregulation of pro-survival pathways. The candidate gene tables provide a focused list for future research. Genes like ENSG00000123983 (upregulated) and ENSG00000172935 (downregulated) represent the most robust changes and are prime targets for experimental validation. Interestingly, the lack of enrichment in any single biological pathway suggests that the resistance mechanism is complex and multifactorial. Rather than hijacking one "master" pathway, the cancer cells appear to make many coordinated changes across a diverse range of cellular functions to collectively achieve a drug-resistant state. Thus, this computational analysis provides a valuable list of candidate genes and reveals a complex, activation-dominant mechanism of drug resistance in this glioblastoma model.

Source: The gene expression data used in this project was obtained from the NCBI Gene Expression Omnibus (GEO) under the accession number [GSE295766](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE295766)

## Reproducing the Analysis
1. Clone this repository.
2. Ensure you have the required libraries by running: `pip install -r requirements.txt`
3. Open and run the `Glioblastoma_Analysis.ipynb` notebook in a Jupyter environment.
