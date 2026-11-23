# Direct_RNA-Seq-Analysis
This repository contains the workflows and downstream analyses used to investigate transcriptomic changes through Oxford Nanopore Technologies (ONT) direct RNA sequencing.

## The analysis integrates three major layers of RNA regulation:
- Differential transcript expression – identification of differentially expressed transcripts.
- Differential poly(A) tail length – characterization of changes in transcript polyadenylation.
- Differential m6A modification – identification and characterization of differential N6-methyladenosine (m6A) modifications.

The three analytical layers were subsequently integrated to identify overlapping molecular changes. Finally, the results were compared with independent transgenerational analysis results to investigate shared molecular signatures.

# Analysis Workflow
The overall analysis consists of five main components:
## 1. Differential Transcript Expression Analysis
This analysis identifies transcripts exhibiting significant expression differences between experimental conditions using ONT direct RNA-seq data.

### Workflow
- Basecalling: Raw ONT sequencing signals were basecalled using Dorado.
- Alignment: Basecalled reads were aligned using Dorado.
- Quantification: Transcript-level read counts were generated using NanoCount.
- Differential expression: Differential transcript expression was assessed using DESeq2.
- Functional enrichment: Enrichment analyses were performed on the identified differentially expressed transcripts to investigate associated biological processes and molecular functions.

### Key outputs
- Transcript-level expression matrices.
- Differential expression results.
- Significantly upregulated and downregulated transcripts.
- Functional enrichment results and biological pathway annotations.

## 2. Differential Poly(A) Tail Length Analysis
This analysis investigates differences in poly(A) tail length between experimental conditions to identify potential changes in post-transcriptional regulation.

### Workflow
- Basecalling: Raw ONT signals were basecalled using Dorado.
- Alignment: Reads were aligned using Dorado.
- Quantification: Poly(A) tail length information was extracted and quantified using samtools.
- Differential analysis: A generalized linear model (GLM) was applied to identify differences in poly(A) tail length between experimental conditions.
- Functional enrichment: Enrichment analysis was conducted to investigate the biological relevance of genes associated with differential poly(A) tail length.

### Key outputs
Poly(A) tail length measurements.
Differential poly(A) tail length statistics.
Genes/transcripts with significantly altered poly(A) tail lengths.
Functional enrichment results.

## 3. Differential m6A Modification Analysis
This analysis focuses on identifying differential N6-methyladenosine (m6A) RNA modifications across experimental conditions.

### Workflow
- Basecalling: Raw ONT signals were basecalled using Dorado.
- Alignment: Reads were aligned using Dorado.
- Differential m6A analysis: Differential m6A modification analysis was performed using modkit.
- Genomic feature annotation: Identified m6A sites were annotated according to their associated genomic features.
- Functional enrichment: Enrichment analysis was performed to characterize the biological functions associated with genes containing differential m6A modifications.

### Key outputs
- Differential m6A modification results.
- Genomic coordinates of differential m6A sites.
- Annotation of m6A sites to genomic features.
- Gene-level m6A modification summaries.
- Functional enrichment results.

##  4. Integrative Analysis of Transcript Expression, Poly(A) Tail Length, and m6A Modification
To investigate the relationships between different layers of RNA regulation, the results from the three independent analyses were integrated.

### Integration strategy
An overlap-based approach was used to identify shared genes or transcripts across:
- Differential transcript expression.
- Differential poly(A) tail length.
- Differential m6A modification.

### The integration aimed to identify:
- Genes exhibiting changes across multiple RNA regulatory layers.
- Shared molecular signatures between different regulatory mechanisms.
- Potential relationships between transcript abundance, poly(A) tail regulation, and m6A modification.
- Genes affected by multiple regulatory processes simultaneously.

### Key outputs
- Pairwise overlaps between the three analyses.
- Three-way overlapping gene sets.
- Venn diagrams and intersection plots.
- Integrated gene lists.
- Functional enrichment of overlapping gene sets.

## 5. Integration with Transgenerational Results
The integrated ONT direct RNA-seq findings were further compared with previously obtained transgenerational analysis results.

### Integration strategy
An overlap-based approach was used to compare the molecular signatures identified in the current analyses with those observed in the transgenerational study.

### This analysis aimed to:
Identify genes shared between the ONT RNA regulatory analyses and transgenerational results.
Identify common molecular signatures potentially associated with transgenerational effects.
Investigate whether changes in transcript expression, poly(A) tail length, and m6A modification overlap with transgenerational molecular findings.

### Key outputs
- Overlapping gene lists.
- Intersection and Venn diagrams.
- Shared molecular signatures.
- Functional enrichment of overlapping genes.

## A suggested organization for the project is:
```text
├── README.md
│
├── data/
│   ├── raw/
│   ├── basecalled/
│   └── aligned/
│
├── scripts/
│   ├── 01_dorado_basecalling.sh
│   ├── 02_dorado_alignment.sh
│   ├── 03_transcript_quantification.sh
│   ├── 04_differential_expression.R
│   ├── 05_polya_quantification.sh
│   ├── 06_differential_polya.R
│   ├── 07_differential_m6a.sh
│   ├── 08_m6a_annotation.R
│   ├── 09_functional_enrichment.R
│   ├── 10_integrative_analysis.R
│   └── 11_transgenerational_integration.R
│
├── results/
│   ├── transcript_expression/
│   ├── polya_tail_length/
│   ├── m6a_modification/
│   ├── enrichment/
│   ├── integrative_analysis/
│   └── transgenerational_integration/
│
└── figures/
    ├── transcript_expression/
    ├── polya_tail_length/
    ├── m6a_modification/
    └── integration/
```
### Reproducibility
The analyses were conducted using a combination of command-line bioinformatics tools and R-based statistical analyses.

### To reproduce the workflows, users should:
- Install the required software and dependencies.
- Prepare ONT direct RNA-seq raw sequencing data.
- Configure reference genome and transcriptome files.
- Run the basecalling and alignment workflows.
- Execute the individual downstream analyses.
- Perform functional enrichment and integrative analyses.

### Software versions, parameter settings, and computational environments should be documented to ensure reproducibility.

### Acknowledgements
This project uses several open-source bioinformatics tools, including Dorado, NanoCount, samtools, DESeq2, and modkit. We acknowledge the developers and maintainers of these tools for making them available to the research community.

### Contact
For questions regarding the analysis or repository, please contact:
Author: Adeolu Ogunleye
Email: adeolu.ogunleye@ebc.uu.se
Institution: Uppsala University
