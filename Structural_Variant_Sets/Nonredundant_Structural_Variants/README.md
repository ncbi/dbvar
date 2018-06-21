# dbVar human non-redundant structural variants (nr SVs)

## Work in progress and subject to change

## Last updated:

06/21/18

## Link to latest nr SV file downloads:

[https://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/](https://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/#github)

# Introduction

NCBI's database of Human Genomic Structural Variation is dbVar.  

  [https://www.ncbi.nlm.nih.gov/dbvar](https://www.ncbi.nlm.nih.gov/dbvar/#github)

An Overview of Structural Variation can be found here:

 [https://www.ncbi.nlm.nih.gov/dbvar/content/overview](https://www.ncbi.nlm.nih.gov/dbvar/content/overview/#github)

## Description of NR SV data files:

* Sets of "non-redundant structural variations" (NR SVs) derived from dbVar are
available via FTP as tab delimited files by assembly, GRCh37 & GRCh38, and type of variant.  

* Non-redundant refers to variant coordinates, i.e. chr, outermost start, and
outermost stop.  Please note: the non-redundant coordinates are based strictly
on exact overlap of coordinates, not on partial overlaps.  

* Other features of NR SV files: 
   * variant calls are from germline samples only (no somatic)
   * placements are "BestAvailable" on the assembly (guarantees no duplicate placements for a variant)
   * placements are on finished chromosomes only (not on NT_ or NW_ contigs)
   * placements are 1-based in the .tsv files 
   * placements are zero-based start and 1-based stop in .bed and .bedpe files (coming soon)
   * insertion_length is set to sequence length if the sequence was submitted to dbVar without a specific insertion_length
   * insertions submitted to dbVar without insertion_length or submitted sequence are not included in the NR files
   
* Other files based on NR SV files:
   * NR SV files annotated with overlapping ACMG genes (more details soon)
   * NR SV files in .bed format (more details soon)
   * NR SV files in .bedpe format (more details soon)

## Variant types

Variant types are grouped into three "aggregation types".  

* deletions
* duplications
* insertions

The variant types in each of the three "aggregation types" are:

* "deletions" include:
   * alu_deletion
   * copy_number_loss
   * deletion
   * line1_deletion
   * sva_deletion

* "duplications" include:
   * copy_number_gain
   * copy_number_variation
   * duplication
   * tandem_duplication

* "insertions" include:
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
**DUPLICATIONS** | |
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
  2207235  | GRCh38.nr_deletions.tsv
   326596  | GRCh38.nr_duplications.tsv
  1101221  | GRCh38.nr_insertions.tsv
  3635052  | total

NR coordinates | GRCh37 nr files
-----------|----------------------------------------------
  2219439  | GRCh37.nr_deletions.tsv
   336634  | GRCh37.nr_duplications.tsv
  1095615  | GRCh37.nr_insertions.tsv
  3651688  | total

# Files

The "NR SVs" are in ASCII text files with tab-separated values on the FTP site.

## Deletion NR SV Files:

* GRCh38.nr_deletions.tsv.gz
* GRCh37.nr_deletions.tsv.gz
* GRCh38.nr_deletions.acmg_genes.tsv.gz
* GRCh37.nr_deletions.acmg_genes.tsv.gz
* GRCh38.nr_deletions.bed.gz
* GRCh38.nr_deletions.bedpe.gz
* GRCh37.nr_deletions.bed.gz
* GRCh37.nr_deletions.bedpe.gz

[https://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/deletions/](https://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/deletions/#github)

## Insertion NR SV Files:

* GRCh38.nr_insertions.tsv.gz
* GRCh37.nr_insertions.tsv.gz
* GRCh38.nr_deletions.acmg_genes.tsv.gz
* GRCh37.nr_deletions.acmg_genes.tsv.gz
* GRCh38.nr_insertions.bed.gz
* GRCh37.nr_insertions.bed.gz
* GRCh38.nr_insertions.bedpe.gz
* GRCh38.nr_insertions.bedpe.gz
* GRCh37.nr_insertions.bedpe.gz

[https://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/insertions/](https://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/insertions//#github)

## Duplication NR SV Files:

* GRCh38.nr_duplications.tsv.gz
* GRCh37.nr_duplications.tsv.gz
* GRCh38.nr_duplications.acmg_genes.tsv.gz
* GRCh37.nr_duplications.acmg_genes.tsv.gz
* GRCh38.nr_duplications.bed.gz
* GRCh37.nr_duplications.bed.gz
* GRCh38.nr_duplications.bedpe.gz
* GRCh37.nr_duplications.bedpe.gz

[https://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/duplications/](https://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/duplications//#github)

# NR Records:

## Records in the NR SV files contain tab-separated fields (only insertion SVs have min and max insertion_length):

| chr | outermost_start | outermost_stop | SV_count | variant_type | method | analysis | platform | study | SV | clincical_assertion | clinvar_accession | min_insertion_length | max_insertion_length |

## Records in the NR SV ACMG files contain tab-separated fields (only insertion SVs have min and max insertion_length):

(update coming soon)

## Records in the NR SV .bed files

(update coming soon)

## Records in the NR SV .bedpe files

(update coming soon)

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

# README files for deletions, insertions, and duplications

Please see README files for deletions, insertions, and duplications for example 
records and additional details.

* Deletions: https://github.com/ncbi/dbvar/blob/master/Structural_Variant_Sets/Nonredundant_Structural_Variants/Deletions/README.md
* Insertions: https://github.com/ncbi/dbvar/blob/master/Structural_Variant_Sets/Nonredundant_Structural_Variants/Insertions/README.md
* Duplications:
https://github.com/ncbi/dbvar/blob/master/Structural_Variant_Sets/Nonredundant_Structural_Variants/Duplications/README.md

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

* Please email dbvar@ncbi.nlm.nih.gov or create an issue on this GitHub page.

# Thanks!

Thanks for your interest in the dbVar human "non-redundant structural variations" (NR SVs)
data files from NCBI.

Please check back soon for further updates.
