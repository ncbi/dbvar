# dbVar Structural Variant (SV) Datasets 

## ****This work is subject to change due to work in progress****

Advances in genomic technologies have revealed structural variations (SV) to be prevalent in all human DNA, and research increasingly implicates SV in phenotypic diversity and disease. Within the next few years millions of genomes will be sequenced, leading to the discovery of millions of SVs that will need to be analyzed to understand their functional impacts. A critical step in variant analysis and interpretation is comparing SV identified in an individual or population with sets of known variants in public databases such as dbVar, to gain biological insights from existing variant annotation and to identify novel variants. This process can be especially difficult without a reference set of variants, representing the sum of current knowledge, to provide a context in which novel variation can be understood. To address this gap, dbVar proposed the creation of a structural variation reference catalog with rich genomic and biological annotations for use in SV analysis, annotation, and related workflows. 

dbVar is an NCBI database of human genomic structural variation that contains more than 5 million submitted SVs from 157 human studies, including data from large diversity projects such as the 1000 Genomes Project and the global population CNV survey (Sudmant et al., 2015), and from clinical sources such as ClinVar and ClinGen. Using this large collection of variants, we created two SV datasets. 

1)	One is an aggregated list of variants in dbVar (i.e. CNV, indel, etc.) derived from large-scale published studies that were conducted by consortia or large collaborations, included high numbers of tested samples, were genome-wide in scope, and applied multiple rigorous methods and analyses.

2)	The second reference dataset is a list of genomic intervals named Structural Variant Clusters (SVC) containing high concentrations of putative ‘common’ structural variation across the genome. SVC are generated using open source software (https://github.com/NCBI-Hackathons/Structural_Variant_Comparison, Phan et al., 2017). 

SVs from both reference datasets were annotated using available data on genes, molecular consequence, clinical significance, dosage sensitivity, and regulatory regions, as well as relevant genomic structural features such as repetitive regions, segmental duplications, and assembly-assembly alignment anomalies. The reference data and annotations are intended to facilitate the integration and comparison of dbVar SV data with other genome annotations (such as disease phenotype and population frequencies) and to provide insights into the impact of the SV on biological functions.

The resulting alpha-release datasets are available in VCF and tab-delimited formats. Our goal is to update these files on a regular basis, incorporating new variant submissions, genomic features, Gene, RefSeq, ClinVar and other annotation information as is becomes available. We encourage users to test these files and to provide feedback to dbVar at dbvar@ncbi.nlm.nih.gov or submit a request in https://github.com/ncbi/dbvar/issues.

============================

 