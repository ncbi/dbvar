# dbVar Non-Redundant Structural Variation Datasets for deletion variants

## ****This work is subject to change due to work in progress****

## Last updated: 
04/04/18

## Link to FTP site: 

ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/human_non_redundant/del

# Introduction

The non-redundant structural variants, "nr SVs", of type "deletion" are in two 
files on the FTP site:

del/all_nr_GRCh37_aggregated_deletion_loss.tsv
del/all_nr_GRCh38_aggregated_deletion_loss.tsv

The variant types in the NR "aggregated deletions and losses" file are:

* alu_deletion
* copy_number_loss
* deletion
* line1_deletion
* sva_deletion

# Records in the aggregated_deletion_loss files 

Records in the aggregated_deletion_loss files contain the following tab-separated fields.

| chr | outer_most_start | outermost_stop | SV_count | variant_type | method | analysis | platform | study | SV |


## Example record 1:

chr | outer_most_start | outermost_stop | SV_count | variant_type | method | analysis | platform | study | SV 
----|------------------|----------------|----------|--------------|--------|----------|----------|-------|---
1 | 10001 | 1535693 | 1  | deletion;  | Oligo_aCGH;  | Probe_signal_intensity; | NA;  | Boone2013;  | nssv1614481;

### Explanation:

* The non-redundant coordinates for this record in dbvar are chr1, with
an outermost start of 10001 and outermost stop of 1535693.

* The SV_count of 1 indicates there is only one SV with an exact match to the 
given placement.  This count does not include SVs with a partial match.

* The variant_call_type is "deletion".

* The method of "Oligo_aCGH" and the analysis of "Probe_signal_intensity" 
indicate how the one variant was evaluated.

* NA indicates the no platform was specified this one deletion variant.

* Boone2013 is the study name as found in dbVar.

* The dbVar variant_accession is "nssv1614481".

* URLs using the study name or variant_accession can be created to access the data
in dbVar, e.g.:
https://www.ncbi.nlm.nih.gov/dbvar/?term=Boone2013
https://www.ncbi.nlm.nih.gov/dbvar/?term=nssv1614481

* From the latter page you may click on the "Variant Region ID" on the left to see
the variant's region in the NCBI Variation Viewer at:

https://www.ncbi.nlm.nih.gov/dbvar/variants/nsv933473/

## Example record 2:

chr | outer_most_start | outermost_stop | SV_count | variant_type | method | analysis | platform | study | SV 
----|------------------|----------------|----------|--------------|--------|----------|----------|-------|---
1 | 72300544 | 72346418 | 7 | copy_number_loss;deletion; | Oligo_aCGH;Sequencing; | Probe_signal_intensity;Read_depth; | Agilent 24M aCGH;Illumina IIx; | Park2010;Ju2010; | nssv1423530:nssv1425248:nssv1428032:nssv1428830:nssv1434173:nssv1439464:nssv1420391;

### Explanation:

* This is a more complicated example deletiion NR record containing multiple 
variants with multiple types, methods, and analyses from multiple studies, using 
multiple platforms.

# Mehods include eg:

* BAC_aCGH
* Curated
* MLPA
* Merging
* Multiple
* Not_provided
* Oligo_aCGH
* Optical_mapping
* ROMA
* SNP_array
* Sequencing
* qPCR
* ROMA
* SNP_array
* Sequencing

# Analyses include, eg:

* Curated
* Genotyping
* Local_sequence_assembly
* Manual_observation
* Merging
* Multiple
* Not_provided
* Optical_mapping
* Other
* Paired-end_mapping
* Probe_signal_intensity
* Read_depth
* Read_depth_and_paired-end_mapping
* SNP_genotyping_analysis
* Sequence_alignment
* Split_read_and_paired-end_mapping
* Split_read_mapping
* de_novo_sequence_assembly

For an overview of all the NR files please see the README at

https://github.com/ncbi/dbvar/tree/master/sandbox/human_non_redundant

# Questions or feedback

For questions or feedback please email John Garner at jg95r@nih.gov

# Thank you!

Thanks for your interest in the dbVar human "non-redundant structural variations" (nr SVs) 
data files from NCBI.

Please check back soon for updates.
