# dbVar human "non-redundant structural variations" (nr SVs) data files

## ****This work is subject to change due to work in progress****

## Last updated: 
04/12/18

## Link to FTP site: 

ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/human_non_redundant/

# Introduction

NCBI's database of Human Genomic Structural Variation is dbVar.  

  https://www.ncbi.nlm.nih.gov/dbvar

An overview of "Structural Variation" is found here:

  https://www.ncbi.nlm.nih.gov/dbvar/content/overview/#datamodel

## Description of data files:

Sets of "non-redundant structural variations" (nr SVs) derived from dbVar are 
available via FTP as tab delimited files by assembly, GRCh37 & GRCh38, and by 
type of variant.  

Non-redundant refers to variant coordinates, i.e. chr, outermost start, and 
outermost stop.  Please note: the non-redundant coordinates are based strictly 
on exact overlap of coordinates, not on partial overlaps.  

## Variant types

Variant types are grouped into three "aggregation types".  

* aggregated deletions and losses
* aggregated duplications and gains
* aggregated insertions

The variant types in each of the three "aggregation types" are:

* "aggregated deletions and losses" include:
   * alu_deletion
   * copy_number_loss
   * deletion
   * line1_deletion
   * sva_deletion

* "aggregated duplications and gains" include:
   * copy_number_gain
   * copy_number_variation
   * duplication
   * tandem_duplication 

* "aggregated insertions" include:
   * alu_insertion
   * insertion
   * line1_insertion
   * mobile_element_insertion
   * novel_sequence_insertion
   * sva_insertion

# Summary Statistics

## Number of input SV by assembly as of Mar 9, 2018:

variant type | GRCh37 | GRCh38
-------------|--------|-------
**DELETIONS** | |
alu_deletion |  1700117 | 1683546
copy_number_loss  |  2409362 | 2392904
deletion |   13091839 | 12903950
herv_deletion |   197 | 197
line1_deletion |  82103 |  81940
sva_deletion |  14254 | 14254
copy_number_variation |  1164548 | 1106074
**DUPLICATIONS and GAINS** | |
duplication |  1926155 | 1915335
tandem_duplication |  11478 |  11446
copy_number_gain	 | 1247923 | 1208729
**INSERTIONS** | |
alu_insertion |  19908 | 19764
insertion |  1220439 | 1226610
line1_insertion |  3916 | 3901
mobile_element_insertion | 88610 | 88773
novel_sequence_insertion | 4067 | 4041
sva_insertion |  1097 |  1087

## NR Coordinates by assembly as of Mar 9, 2018:

NR coordinates | GRCh38 nr files
-----------|----------------------------------------------
  2207235  | all_nr_GRCh38_aggregated_deletion_loss.tsv 
   326596  | all_nr_GRCh38_aggregated_duplication_gain.tsv
  1101221  | all_nr_GRCh38_aggregated_insertions.tsv
  3635052  | total

NR coordinates | GRCh37 nr files
-----------|----------------------------------------------
  2219439  | all_nr_GRCh37_aggregated_deletion_loss.tsv
   336634  | all_nr_GRCh37_aggregated_duplication_gain.tsv
  1095615  | all_nr_GRCh37_aggregated_insertions.tsv
  3651688  | total

# Files

The "nr SVs" will be in six ASCII text files with tab-separated values on the 
FTP site.

## Files available now:

* del/all_nr_GRCh37_aggregated_deletion_loss.tsv
* del/all_nr_GRCh38_aggregated_deletion_loss.tsv

ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/human_non_redundant/del

* ins/all_nr_GRCh37_aggregated_insertions.tsv  
* ins/all_nr_GRCh38_aggregated_insertions.tsv  

ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/human_non_redundant/ins

## Files coming a bit later:

* dup/all_nr_GRCh37_aggregated_duplication_gain.tsv  
* dup/all_nr_GRCh38_aggregated_duplication_gain.tsv  

# Example NR Records: 

## Records in the aggregated_deletion_loss files 

Records in the aggregated_deletion_loss files contain the following tab-separated fields.

| chr | outermost_start | outermost_stop | SV_count | variant_type | method | analysis | platform | study | SV |


## Example record 1:

chr | outermost_start | outermost_stop | ssv_count | variant_type | method | analysis | platform | study | ssv 
----|------------------|----------------|----------|--------------|--------|----------|----------|-------|---
1 | 10001 | 1535693 | 1  | deletion | Oligo_aCGH  | Probe_signal_intensity | NA  | Boone2013  | nssv1614481

### Explanation:

* The non-redundant coordinates for this record in dbVar are chr1, with
an outermost start of 10001 and outermost stop of 1535693.

* The ssv_count of 1 indicates there is only one ssv with an exact match to the 
given placement.  This count does not include ssvs with a partial match.

* The variant_call_type is "deletion".

* The method of "Oligo_aCGH" and the analysis of "Probe_signal_intensity" 
indicate how the one variant was evaluated.

* NA indicates the no platform was specified for this one deletion variant.

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

chr | outermost_start | outermost_stop | ssv_count | variant_type | method | analysis | platform | study | ssv 
----|------------------|----------------|----------|--------------|--------|----------|----------|-------|---
1 | 72300544 | 72346418 | 7 | copy_number_loss;deletion | Oligo_aCGH;Sequencing | Probe_signal_intensity;Read_depth | Agilent 24M aCGH;Illumina IIx | Park2010;Ju2010 | nssv1423530:nssv1425248:nssv1428032:nssv1428830:nssv1434173:nssv1439464:nssv1420391

### Explanation:

* This is a more complicated example deletion NR record containing multiple 
variants with multiple types, methods, and analyses from multiple studies, using 
multiple platforms.

# Methods include e.g.:

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

# Analyses include, e.g.:

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

# README files for deletion, insertions, and duplications and gains

Please see README files for deletions, insertions, and duplications and gains, 
additional details.

* deletions README: https://github.com/ncbi/dbvar/blob/master/sandbox/human_non_redundant/del/README_del.md
* insertions README: https://github.com/ncbi/dbvar/blob/master/sandbox/human_non_redundant/del/README_ins.md
* duplications and gains README: coming a bit later

# Brief Outline of algorithm used to generate NR-SVs.

The algorithm makes use of previously existing scripts.

Input files are generated from the dbVar database with tab separated values and
contain SVs by assembly, type, and other relevant fields.

Selected type files are grouped into "aggregated type files" as specified above, 
by chr.

The "aggregated type files" are converted into XML records containing all the 
neccessary fields required by the nr process.

The XML is then parsed to generate SV records with coordinates, type, 
method, analysis, platform, insertion_length, SV accession and study.  

The SV records are then proccessed to generate the NR records described above. 

# Questions or feedback

* Please email John Garner at dbvar-dev@ncbi.nlm.nih.gov
* Please create an issue on this GitHub page.

# Thanks!

Thanks for your interest in the dbVar human "non-redundant structural variations" (nr SVs) 
data files from NCBI.

Please check back for updates soon.

