# dbVar human non-redundant structural variants (nr SVs)

## Work in progress and subject to change

**Last updated:** 07/13/18


## Latest nr SV file downloads:

[https://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/](https://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/#github)

## Tutorial on how to use dbVar nr SV files:
[https://github.com/ncbi/dbvar/blob/master/Structural_Variant_Sets/Nonredundant_Structural_Variants/UserExamples.md](https://github.com/ncbi/dbvar/blob/master/Structural_Variant_Sets/Nonredundant_Structural_Variants/UserExamples.md)

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
   * placements are zero-based start and 1-based stop in .bed and .bedpe files
   * insertion_length is set to sequence length if the sequence was submitted to dbVar without a specific insertion_length
   * insertions submitted to dbVar without insertion_length or submitted sequence are not included in the NR files

* Other files based on NR SV files:
   * NR SV files annotated with overlapping ACMG genes
   * NR SV files in .bed format
   * NR SV files in .bedpe format

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
   * herv_deletion
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

## Number of input SV by assembly as of Jul 11, 2018:

variant type | GRCh37 | GRCh38
:-----------:|:------:|:-----:
**DELETIONS** | |
alu_deletion |  1700117 | 1683546
copy_number_loss  |  2409362 | 2392904
deletion |   13091839 | 12903950
herv_deletion |   197 | 197
line1_deletion |  82103 |  81940
sva_deletion |  14254 | 14254
**DUPLICATIONS** | |
copy_number_gain	 | 1247923 | 1208729
copy_number_variation |  1164548 | 1106074
duplication |  1926155 | 1915335
tandem_duplication |  11478 |  11446
**INSERTIONS** | |
alu_insertion |  19908 | 19764
insertion |  1220439 | 1226610
line1_insertion |  3916 | 3901
mobile_element_insertion | 88610 | 88773
novel_sequence_insertion | 4067 | 4041
sva_insertion |  1097 |  1087

## NR Coordinates by assembly as of Jul 11, 2018:

GRCh38 nr files | NR coordinates | GRCh37 nr files | NR coordinates |
:---------:|:--------------------------:|:---------:|:--------------------------:
GRCh38.nr_deletions.tsv |  2207235  | GRCh37.nr_deletions.tsv | 2219439 |
GRCh38.nr_duplications.tsv | 326596  | GRCh37.nr_duplications.tsv | 336634  |
GRCh38.nr_insertions.tsv | 1101221  | GRCh37.nr_insertions.tsv |  1095615  |
total: |3635052  | total: | 3651688  |

# NR SV Files

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

# NR Records contain tab-separated fields:

## Please note: 
* The fields type, method, analysis, platform, variant, study, clinical_significance, clinvar_accession, and gene may contain multiple values.  
* Each of the values is associated with one or more calls found in the variant field.  
* The values in the variant field are "dbVar call accessions". 

## Records in the deletions or duplications NR SV files, e.g.:  

| chr | outermost_start | outermost_stop | variant_count | variant_type | method | analysis | platform | study | variant | clincical_assertion | clinvar_accession |
----|-----------------|----------------|---------------|--------------|--------|----------|----------|-------|-------------|-------------------|-------------------|
15 | 98085101 | 101843270 | 1 | copy_number_loss | Oligo_aCGH | Probe_signal_intensity | Agilent ISCA 44K | ClinGen_Laboratory-Submitted | nssv14082018 | Pathogenic | SCV000586438

## Records in the insertions NR SV files, e.g.:

| chr | outermost_start | outermost_stop | variant_count | variant_type | method | analysis | platform | study | variant | clincical_assertion | clinvar_accession | min_insertion_length | max_insertion_length |
----|-----------------|----------------|---------------|--------------|--------|----------|----------|-------|-------------|-------------------|-------------------|----------------------|----------------------
1 | 1889055 | 1889055 | 1 | alu_insertion | Sequencing | Split_read_and_paired-end_mapping | HiSeq 2000 | Gardner2017 | nssv14051747 |  |  | 258 | 258

* only insertion SVs have minimum_insertion_length and maximum_insertion_length fields

## Records in the NR SV ACMG files contain a field for the ACMG gene that overlaps the variant, e.g.:

chr | outermost_start | outermost_stop | variant_count | variant_type | method | analysis | platform | study | variant | clinical_significance | clinvar_accession | min_insertion_length | max_insertion_length | gene
----|-----------------|----------------|---------------|--------------|--------|----------|----------|-------|-------------|-------------------|-------------------|----------------------|----------------------|-----
3| 30621876 | 30621876 | 2 | alu_insertion | Merging;Sequencing | Merging;Split_read_and_paired-end_mapping | See merged experiments;HiSeq 2000 | 1000_Genomes_Consortium_Phase_3_SV_Submission;Gardner2017 | essv18243203;nssv14059593 |  |  |279 | 280 | TGFBR2 

### Caveats for the ACMG files:

* ACMG files are provided as a "proof of principle" for a "use case" for the NR SV files.
* ACMG files are based on region/gene overlaps, and are missing a few call/gene overlaps in the cases where the parent variant region does not include all of the variant call placement and the region does not overlap the gene or is upstream or downstream of the gene.   
* Placements in the ACMG files do not account for confidence intervals, even though the overlaps reported in the file were determined using confidence intervals. This results in a few of the overlaps that are not supported by the placements as reported in the file.

For information on ACMG genes please see:
https://www.ncbi.nlm.nih.gov/clinvar/docs/acmg/

## Records in the NR SV .bed files, e.g.

chr | outermost_start | outermost_stop | name  
----|-----------------|----------------|-----
chr1 | 0 | 10000 | chr1_0_10000_del

* Placements in bed files are zero-based start and one-based stop
* name is comprised of chromosome, outermost_start, outermost_stop, and type (del, dup, or ins)
* NR SV .bed files may be used with a variety of tools as shown in the tutorial:

[https://github.com/ncbi/dbvar/blob/master/Structural_Variant_Sets/Nonredundant_Structural_Variants/UserExamples.md](https://github.com/ncbi/dbvar/blob/master/Structural_Variant_Sets/Nonredundant_Structural_Variants/UserExamples.md)

## Records in the NR SV .bedpe files, e.g.

chrom1 | start1 | end1 | chrom2 | start2 | end2 | name | score | strand1 | strand2 | variant_count | variant_type | method | analysis | platform | study | variant | clinical_assertion | clinvar_accession
-------|--------|------|--------|--------|------|------|-------|---------|---------|----------|--------------|--------|----------|----------|-------|----|--------------------|------------------
chr1 | 14873 | 7527302 | . | -1 | -1 | chr1_14873_7527302_del | . | . | . | 1 | copy_number_loss | Oligo_aCGH | Probe_signal_intensity | NA | ClinGen_Laboratory-Submitted | nssv13638713 | Pathogenic | SCV000495999

* Placements in bedpe files are zero-based start and one-based stop
* bedpe files are normally used for disjointed genomic sequences
* the NR bedpe files do not contain disjointed genomic sequences, and instead use default values for chrom2, start2 and end2 
* the NR bedpe files use the optional fields starting at field 11 to hold: chr, outermost_start, outermost_stop, name, and all the additional fields which are in the NR SV files  

# Methods and Analyses 
## example values

| Methods include, e.g. | Analyses include, e.g. |
|:--------------------:|:--------------------:|
| BAC_aCGH | Curated |
| Curated | Genotyping |
| MLPA | Local_sequence_assembly |
| Merging | Merging |
| Multiple | Multiple |
| Not_provided | Not_provided |
| Oligo_aCGH | Optical_mapping |
| Optical_mapping | Other |
| ROMA | Paired-end_mapping |
| SNP_array | Probe_signal_intensity |
| Sequencing | Read_depth |
| qPCR | SNP_genotyping_analysis |
| ROMA | Sequence_alignment |
| SNP_array | Split_read_mapping |
| Sequencing | de_novo_sequence_assembly |

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

The SV records are then processed to generate NR SV tab-separated value (tsv) files by assembly and type, as described above, e.g. 
* GRCh38.nr_deletions.tsv.gz

# Tutorials

Examples of using the NR files with various tools and browsers can be found in: https://github.com/ncbi/dbvar/blob/master/Structural_Variant_Sets/Nonredundant_Structural_Variants/UserExamples.md

# Questions or feedback

* Please email dbvar@ncbi.nlm.nih.gov or create an issue on this GitHub page.

# Thanks!

Thanks for your interest in the dbVar human "non-redundant structural variations" (NR SVs)
data files from NCBI.

Please check back soon for further updates.
