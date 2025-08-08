# Olaparib Resistance Analysis
A project by Sean Fan 08/06/25


Abstract:

Acquired resistance to chemotherapy is a major clinical challenge in treating glioblastoma. This project aimed to identify and compare genes associated with resistance to two different drugs, Olaparib and Temozolomide (TMZ), by analyzing two public gene expression datasets (GSE295766 and GSE100736). A bioinformatics procedure in Python was used to perform a differential expression analysis for each study. The Olaparib study revealed 263 significantly upregulated and 403 significantly downregulated genes. The TMZ study showed a much broader response, with 3185 upregulated and 7287 downregulated genes. A direct comparison of the top candidate genes and the full significant lists revealed zero overlapping upregulated genes, leading to the conclusion that the genetic mechanisms of resistance are highly specific to the therapeutic agent used.

Introduction:

Glioblastoma is an aggressive form of brain cancer with poor patient outcomes, which is largely due to therapeutic resistance. Drugs like Olaparib and Temozolomide (TMZ) are often used in treatment, but cancer cells often adapt and survive. Understanding the genetic changes that drive resistance is critical for designing better therapies. This project investigates this phenomenon by analyzing two public datasets to answer the question: Are there common genes or pathways that drive resistance to different chemotherapy drugs in glioblastoma?

Methods:

A comparative analysis was conducted using two datasets from the NCBI Gene Expression Omnibus:

GSE295766: Olaparib-resistant vs. sensitive U87 glioblastoma cells.

GSE100736: Temozolomide (TMZ)-resistant vs. sensitive U251 glioblastoma cells.

For each dataset, a pipeline in a Jupyter Notebook using Python, pandas, and SciPy was executed to clean the data, calculate the Log2 Fold Change (Log2FC) and p-values for each gene, and identify significantly changed genes (defined as Log2FC > |1| and p-value < 0.05). The resulting gene lists were then compared.

Results:

Study 1: Olaparib Resistance Analysis
The analysis of the Olaparib dataset identified 263 significantly upregulated and 403 significantly downregulated genes. The volcano plot (Figure 1) visually confirms this result, showing a distinct population of red (upregulated) and blue (downregulated) dots that have crossed the significance thresholds. The response appears asymmetric, with the upregulated genes generally showing a greater magnitude of change (further from the center) and higher statistical significance (higher on the y-axis) than the downregulated genes. The top candidate genes from this analysis are shown in Tables 1 and 2.

Figure 1: 
<img width="2960" height="2343" alt="volcano_plot" src="https://github.com/user-attachments/assets/e5da23d6-3206-491b-984c-ad01266cc9be" />
Volcano plot visualizing gene expression changes in response to Olaparib.

Study 2: Temozolomide (TMZ) Resistance Analysis
The analysis of the TMZ dataset revealed a much broader and more dramatic genetic response, with 3185 significantly upregulated and 7287 significantly downregulated genes. The volcano plot (Figure 2) illustrates this massive shift in the cell's genetic programming, with a dense cloud of both red and blue dots far exceeding the significance thresholds. Unlike the Olaparib study, the response to TMZ appears more symmetrical, with a large number of genes being both activated and silenced.

Figure 2:
<img width="2983" height="2343" alt="volcano_plot_tmz" src="https://github.com/user-attachments/assets/aa43c7c8-3e20-423a-a7dd-a749f8a22689" />
Volcano plot visualizing gene expression changes in response to TMZ.

Candidate Gene Analysis:

A direct comparison of the top 10 candidate genes from each study highlights the drug-specific nature of the response.

Table 1: Top 10 most upregulated genes in Olaparib-resistant cells.
<img width="2996" height="636" alt="top_10_upregulated_genes" src="https://github.com/user-attachments/assets/49d5eadf-0a29-4590-a52d-acb8e6dfd90e" />

Table 2: Top 10 most upregulated genes in TMZ-resistant cells.
<img width="4524" height="753" alt="top_10_upregulated_tmz" src="https://github.com/user-attachments/assets/750642e6-042d-4dc9-b15b-d9bf32905f02" />

Table 3: Top 10 most downregulated genes in Olaparib-resistant cells.
<img width="2996" height="636" alt="top_10_downregulated_genes" src="https://github.com/user-attachments/assets/8fef9135-53b4-4cba-8d4c-ffe5b6ffd097" />

Table 4: Top 10 most downregulated genes in TMZ-resistant cells.
<img width="4524" height="753" alt="top_10_downregulated_tmz" src="https://github.com/user-attachments/assets/a6c1189c-6ba8-400d-bd40-bc4ac54ad47e" />

Discussion and Conclusion:

This project successfully identified thousands of candidate genes involved in drug resistance across two different glioblastoma models. A direct comparison of the results reveals several key insights.

Contrast in Response:

The most important difference is the scale and nature of the response. Olaparib resistance is characterized by a focused and asymmetric response, with a few hundred genes being altered, primarily through activation. In contrast, TMZ resistance triggers a massive, systemic overhaul of the cell's genetic programming, affecting over 10,000 genes through both activation and silencing.

Drug-Specific Gene Sets: 

The detailed analysis of the candidate gene tables (Tables 1-4) confirms the conclusion from the volcano plots: the genetic mechanisms of chemotherapy resistance appear to be highly specific to the drug used. The complete lack of overlapping genes in the top 10 up- and down-regulated lists suggests that the cancer cells are not activating a single, universal resistance program. Instead, they deploy distinct and specialized genetic strategies to counter different therapeutic attacks.

A Deeper Dive into the Biology of Top Candidate Genes:

A functional analysis of the top statistically significant candidate from each category further highlights these different strategies:

Olaparib Upregulated: CHRM3 (Cholinergic Receptor Muscarinic 3): This receptor is known to promote cell proliferation. Its dramatic upregulation suggests that the cancer cells may have become hypersensitive to growth signals to out-divide the damaging effects of Olaparib.

Olaparib Downregulated: DEPP1 (DEPP Autophagy Regulator 1): This gene is a key player in autophagy, a process that leads to programmed cell death. By silencing this gene, the cancer cells may have disabled their own self-destruct mechanism, allowing them to survive DNA damage.

TMZ Upregulated: AVPR1A (Arginine Vasopressin Receptor 1A): This cell surface receptor's upregulation suggests the cancer cells are hijacking the vasopressin signaling pathway to promote their own growth and survival against TMZ.

TMZ Downregulated: SSTR1 (Somatostatin Receptor 1): SSTR1 is a receptor for a hormone that inhibits cell growth. By removing these "stop growing" receptors, the TMZ-resistant cells can effectively ignore natural inhibitory signals, enabling uncontrolled proliferation.

Final Conclusion:

The biological analysis reinforces the overall conclusion. The drug-specific changes—activating growth receptors in one case versus silencing growth inhibitors in another, help highlight the different strategies cancer cells use to survive. This is a critical insight, as it implies that therapies designed to reverse drug resistance may need to be tailored to the specific chemotherapy regimen a patient has received. The lists of specific genes generated in this study provide a valuable starting point for future laboratory research to validate these candidates and explore their precise roles in drug resistance.


Source: The gene expression data used in this project was obtained from the NCBI Gene Expression Omnibus (GEO) and includes two separate datasets:

Olaparib Resistance Study: GSE295766 (https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE295766) 

Temozolomide (TMZ) Resistance Study: GSE100736 (https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE100736)

## Reproducing the Analysis
1. Clone this repository.
2. Ensure you have the required libraries by running: `pip install -r requirements.txt`
3. Open and run the Run the Notebooks:
   -  Glioblastoma_Analysis.ipynb: This notebook performs the initial analysis on the Olaparib dataset (GSE295766).
   -  Comparative_Analysis_TMZ.ipynb: This notebook performs the analysis on the Temozolomide dataset (GSE100736) and compares the results to the first study.
