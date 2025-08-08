# Olaparib Resistance Analysis
A project by Sean Fan 08/06/25

Abstract:

Acquired resistance to chemotherapy is a major clinical challenge in treating glioblastoma. This project aimed to identify and compare genes associated with resistance to two different drugs, Olaparib and Temozolomide (TMZ), by analyzing two public gene expression datasets (GSE295766 and GSE100736). A bioinformatics pipeline in Python was used to perform a differential expression analysis for each study. The Olaparib study revealed 263 significantly upregulated and 403 significantly downregulated genes. The TMZ study showed a much broader response, with 3185 upregulated and 7287 downregulated genes. A direct comparison of the top candidate genes and the full significant lists revealed zero overlapping upregulated genes and a similarly negligible overlap in downregulated genes, leading to the conclusion that the genetic mechanisms of resistance are highly specific to the therapeutic agent used.

Introduction:

Glioblastoma is an aggressive form of brain cancer with poor patient outcomes, largely due to therapeutic resistance. Drugs like Olaparib and Temozolomide (TMZ) are used in treatment, but cancer cells often adapt and survive. Understanding the genetic changes that drive resistance is critical for designing better therapies. This study investigates this phenomenon by analyzing two public datasets to answer the question: Are there common genes or pathways that drive resistance to different chemotherapy drugs in glioblastoma?

Methods:

A comparative analysis was conducted using two datasets from the NCBI Gene Expression Omnibus:

GSE295766: Olaparib-resistant vs. sensitive U87 glioblastoma cells.

GSE100736: Temozolomide (TMZ)-resistant vs. sensitive U251 glioblastoma cells.

For each dataset, a pipeline in a Jupyter Notebook using Python, pandas, and SciPy was executed to clean the data, calculate the Log2 Fold Change (Log2FC) and p-values for each gene, and identify significantly changed genes (defined as Log2FC > |1| and p-value < 0.05). The resulting gene lists were then compared.

Results:

Study 1: Olaparib Resistance
The analysis of the Olaparib dataset identified 263 significantly upregulated and 403 significantly downregulated genes. The genetic response was asymmetric, with the upregulated genes showing a greater magnitude of change.

Figure 1: 
<img width="2960" height="2343" alt="volcano_plot" src="https://github.com/user-attachments/assets/723d1d79-9e45-438d-ae77-aa7293ae7199" />
Volcano plot visualizing gene expression changes in response to Olaparib.

Study 2: Temozolomide (TMZ) Resistance
The analysis of the TMZ dataset revealed a much broader and more dramatic genetic response, with 3185 significantly upregulated and 7287 significantly downregulated genes.

FIgure 2:
<img width="2983" height="2343" alt="volcano_plot_tmz" src="https://github.com/user-attachments/assets/d36bd017-ef65-417b-91ac-1e0e97184d1f" />
Volcano plot visualizing gene expression changes in response to TMZ.

Candidate Gene Analysis:

The top 10 genes with the largest increase and decrease in expression are detailed in Table 1 and Table 2, respectively. These tables distinguish between genes with a large fold change and those that are also statistically significant.

Table 1: 
<img width="2996" height="636" alt="top_10_upregulated_genes" src="https://github.com/user-attachments/assets/3b1e7174-9115-4297-aff0-ecab546de82e" />
The top 10 most upregulated genes, ranked by Log2 Fold Change. Of this list, the top statistically significant candidate is ENSG00000123983, with a large fold change (6.58) and a strong p-value (0.02).

Table 2: 
<img width="4524" height="753" alt="top_10_upregulated_tmz" src="https://github.com/user-attachments/assets/492b1e66-2623-4032-bc76-e3f896de3aaf" />
Top 10 most upregulated genes in TMZ-resistant cells. This list is dominated by different genes, such as IL6 and CXCL8, known for their roles in inflammation. There is no overlap between the top genes in Table 1 and Table 2.

Table 3: 
<img width="2996" height="636" alt="top_10_downregulated_genes" src="https://github.com/user-attachments/assets/756a4fd6-6a58-48f9-9571-442659a48c36" />
Top 10 most downregulated genes in Olaparib-resistant cells. The top candidate is ENSG00000165507, with a large and statistically significant fold change (-6.60).

Table 4:
<img width="4524" height="753" alt="top_10_downregulated_tmz" src="https://github.com/user-attachments/assets/26254690-7d6a-45c1-a4d3-cbdcb5501aae" />
Top 10 most downregulated genes in TMZ-resistant cells. Again, a completely different set of genes is present, such as NPY1R and SSTR1. There is no overlap between the top genes in Table 3 and Table 4.

Discussion and Conclusion
This project successfully identified thousands of candidate genes involved in drug resistance across two different glioblastoma models. The key finding from both the volcano plots and the detailed analysis of the candidate gene tables is that the genetic mechanisms of chemotherapy resistance appear to be highly specific to the drug used.

The complete lack of overlapping genes in the top 10 up- and down-regulated lists is a powerful piece of evidence. It demonstrates that the cancer cells are not activating a single, universal resistance program. Instead, they deploy distinct and specialized genetic strategies to counter different therapeutic attacks. For example, Olaparib resistance is associated with genes like ENSG00000123983, while TMZ resistance involves inflammatory genes like IL6.

This is a critical insight, as it implies that therapies designed to reverse drug resistance may need to be tailored to the specific chemotherapy regimen a patient has received, as a "one-size-fits-all" approach is unlikely to be effective. The lists of specific genes generated in this study provide a valuable starting point for future laboratory research to validate these candidates and explore their precise roles in enabling cancer cells to survive treatment.

Source: The gene expression data used in this project was obtained from the NCBI Gene Expression Omnibus (GEO) and includes two separate datasets:

Olaparib Resistance Study: GSE295766 (https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE295766) 

Temozolomide (TMZ) Resistance Study: GSE100736 (https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE100736)

## Reproducing the Analysis
1. Clone this repository.
2. Ensure you have the required libraries by running: `pip install -r requirements.txt`
3. Open and run the Run the Notebooks:
   -  Glioblastoma_Analysis.ipynb: This notebook performs the initial analysis on the Olaparib dataset (GSE295766).
   -  Comparative_Analysis_TMZ.ipynb: This notebook performs the analysis on the Temozolomide dataset (GSE100736) and compares the results to the first study.
