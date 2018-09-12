# Quick Start


## A guide to using dbVar non-redundant structural variant (NR-SV) data and annotations

**Updated** September 12, 2018


----------



The ***Use Cases*** below illustrate some of the ways dbVar NR SV data and associated annotations can be used. Please send feedback and any questions to dbvar-dev@ncbi.nlm.nih.gov.

dbVar NR data are provided in GRCh37 and GRCh38 coordinates in TSV, BED, and BEDPE formats. Please choose the file(s) best suited your application. For example, BED files are easy to compute on but are lightweight and lack metadata such as clinical assertions that may be useful to your analysis.

**NOTE:** At the present time not all clinical SV in ClinVar have yet been ported to dbVar. In addition, clinical assertions contained in NR-SV datasets are not diagnostic and should be interpreted with caution. For more information please visit [ClinVar's Clinical Significance](https://www.ncbi.nlm.nih.gov/clinvar/docs/clinsig/) informational page.

#### Disclaimer

The information on this website is not intended for direct diagnostic use or medical decision-making without review by a genetics professional. Individuals should not change their health behavior solely on the basis of information contained on this website. NIH does not independently verify the submitted information. If you have questions about the information contained on this website, please see a health care professional. More information about [NCBI's disclaimer policy](https://www.ncbi.nlm.nih.gov/About/disclaimer.html) is available.




----------

## Use Cases:
<!-- TOC depthFrom:3 depthTo:3 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Obtain human clinically-relevant CNVs](#obtain-human-clinically-relevant-cnvs)
- [Find overlaps between NR-SV and candidate structural variants](#find-overlaps-between-nr-sv-and-candidate-structural-variants)
- [Find overlaps between NR SVs and annotation datasets](#find-overlaps-between-nr-svs-and-annotation-datasets)

<!-- /TOC -->

----------

### Obtain human clinically-relevant CNVs

#### Objectives:
* Group NR SV records with clinically-relevant CNVs by assembly and by type
* To obtain clinically-relevant NR SVs in bedpe format so they may be used for further investigation, e.g., to:
  * determine genome locations where pathogenic copy number loss variants are found in dbVar
  * determine overlaps between these these variants and a candidate set of variants

#### Summary of Results:
Using the process described in this use case the following results were obtained on Aug 20, 2018:

Two files of NR SVs, each NR SV containing at least one clinically relevant CNV,
were generated for assembly GRCh37, one for copy_number_loss, and one for copy_number_gain.


| NR SV file | Records with clinical_significance |
|:--------------------------------------:|:----------------------------------:|
| GRCh37.copy_number_gain.with_SCV.bedpe | 13016 |
| GRCh37.copy_number_loss.with_SCV.bedpe | 10872 |


As an example of further processing of the output files, here is a table showing counts of
NR SV records with pathogenic clinical_signicance:


| Count | GRCh37 gains | GRCh37 losses |
|:---------------------:|:---------------------:|:---------------------:|
|records with Pathogenic only|1974|3939|
|records with Pathogenic and another clinical_significance|44|48|
|records with one or more Pathogenic|2018|3987|
| **Total records with clinical significance** | **13016** | **10872** |



##### 1. Get an overview of dbVar NR SV files.  Please note in particular the sections:
* Introduction
* Variant Types
* NR SV Files
* NR Records contain tab-separated fields
* Records in the NR SV .bedpe files
* README files for deletions, insertions, and duplications

[https://github.com/ncbi/dbvar/tree/master/Structural_Variant_Sets/Nonredundant_Structural_Variants](https://github.com/ncbi/dbvar/tree/master/Structural_Variant_Sets/Nonredundant_Structural_Variants)
##### 2. Go to ftp site for deletions:
[https://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/deletions/](https://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/deletions/)

##### 3. Download deletions bedpe file:
###### GRCh37.nr_deletions.bedpe.gz
##### 4. Get human clinically-relevant copy_number_loss records from deletions bedpe file in Linux/UNIX environment:
```markdown
zcat GRCh37.nr_deletions.bedpe.gz | grep SCV > GRCh37.copy_number_loss.with_SCV.bedpe
```
##### 5. Go to ftp site for duplications:
[https://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/duplications/](https://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/duplications/)
##### 6. Download duplications bedpe file:
###### GRCh37.nr_duplications.bedpe.gz

##### 7. Get human clinically-relevant copy_number_gain records from deletions bedpe file in Linux/UNIX environment:
```markdown
zcat GRCh37.nr_duplications.bedpe.gz | grep SCV > GRCh37.copy_number_gain.with_SCV.bedpe
```
##### 8. To further process downloaded files, see "Tutorial - How to Use dbVar's NR SV Data Files":
[https://github.com/ncbi/dbvar/blob/master/Structural_Variant_Sets/Nonredundant_Structural_Variants/UserExamples.md](https://github.com/ncbi/dbvar/blob/master/Structural_Variant_Sets/Nonredundant_Structural_Variants/UserExamples.md)

##### 9.  Using dbVar and ClinVar accessions from the bedpe files to access dbVar and ClinVar

##### dbVar:

URLs using the dbVar accessions obtained in the bedpe files can be created to access the data in dbVar, e.g.:

[https://www.ncbi.nlm.nih.gov/dbvar/?term=nssv13649440](https://www.ncbi.nlm.nih.gov/dbvar/?term=nssv13649440)

From the latter page you may click on the "Variant Region ID" on the left to see the variant's region in the NCBI Variation Viewer at:

[https://www.ncbi.nlm.nih.gov/dbvar/variants/nsv533950/](https://www.ncbi.nlm.nih.gov/dbvar/variants/nsv533950/)

##### ClinVar:

An SCV accession obtained from the bedpe files, e.g. SCV000045941, can be used to find the record in ClinVar by searching for the SCV on ClinVar's home page:

[https://www.ncbi.nlm.nih.gov/clinvar/](https://www.ncbi.nlm.nih.gov/clinvar/)


----------

### Find overlaps between NR-SV and candidate structural variants
This case may be helpful if you would like to know if candidate structural variants compare to existing variants in dbVar.
#### 1. Format your file or candidate structural variants as either gff, bed, or bedpe
For example:
variant_calls.gff:
```markdown
chr13   dbVar   copy_number_gain        100217593       100233402       .       +       .       ID=chr13_100217593_100233402_copy_number_gain_1
chr10   dbVar   copy_number_loss        78342182        78366362        .       +       .       ID=chr10_78342182_78366362_copy_number_loss_1
chr5    dbVar   copy_number_loss        113158233       113172463       .       +       .       ID=ch
```
#### 2. Download NR files
Visit these directories to select the appropriate files according to assembly (GRCh37, GRCh38), or type (bed, bedpe):

[ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/deletions](ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/deletions)

[ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/duplications](ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/duplications)

[ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/insertions](ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/insertions)

NOTE: the .bedpe files have the most information about the variants, however, you can use .bedpe if you only care about the placements. Refer to https://github.com/ncbi/dbvar/tree/master/Structural_Variant_Sets/Nonredundant_Structural_Variants for list of columns included in the files.

For example, bedpe files on GRCh37:

[ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/deletions/GRCh37.nr_deletions.bedpe.gz](ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/deletions/GRCh37.nr_deletions.bedpe.gz)

[ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/duplications/GRCh37.nr_duplications.bedpe.gz](ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/duplications/GRCh37.nr_duplications.bedpe.gz)

[ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/insertions/GRCh37.nr_insertions.bedpe.gz](ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/insertions/GRCh37.nr_insertions.bedpe.gz)


#### 3. NR files
```markdown
gunzip GRCh37.nr_deletions.bedpe.gz
gunzip GRCh37.nr_duplications.bedpe.gz
gunzip GRCh37.nr_insertions.bedpe.gz
```
#### 4. Run bedtools against each NR file
For example, default to any overlap:
```markdown
bedtools intersect -a variant_calls.gff -b GRCh37.nr_deletions.bedpe
bedtools intersect -a variant_calls.gff -b GRCh37.nr_duplications.bedpe
bedtools intersect -a variant_calls.gff -b GRCh37.nr_insertions.bedpe
```
Example of narrower selection criteria, using at least 75% reciprocal overlap, and saving columns from both files to an output file:
```markdown
bedtools intersect -a variant_calls.gff -b GRCh37.nr_deletions.bedpe -wo -r -f .75 > variant_calls_X_nr_deletions.gff
bedtools intersect -a variant_calls.gff -b GRCh37.nr_duplications.bedpe -wo -r -f .75 > variant_calls_X_nr_duplications.gff
bedtools intersect -a variant_calls.gff -b GRCh37.nr_insertions.bedpe -wo -r -f .75 > variant_calls_X_nr_insertions.gff
```
#### 5. Interpret results:

For example, identify unique copy_number_loss variants with >75% reciprocal overlap with NR deletions:
```markdown
cut -f 9 variant_calls_X_nr_deletions.gff | sort -u | grep loss | wc -l
675
```

Identify unique copy_number_gain variants with >75% reciprocal overlap with NR deletions:
```markdown
cut -f 9 variant_calls_X_nr_duplications.gff | grep gain | sort -u | wc -l
558
```

Identify any variants with >75% reciprocal overlap to an NR variant with clinical significance of Pathogenic:
```markdown
grep SCV variant_calls_X_nr_*.gff | grep Pathogenic
chr16    dbVar   copy_number_loss        14945195    16363239 .       +       .       ID=chr16_14945195_16363239_copy_number_loss_1   chr16   14809981     16477578        .       -1      -1      chr16_14809981_16477578_del     .       .       .   copy_number_loss Oligo_aCGH      Probe_signal_intensity  NA      ClinGen_Laboratory-Submitted nssv585211;nssv3396567  Pathogenic      SCV000175002    large   .       .       1418045
```
Using the -wo option to bedtools intersect returns the full set of columns from the NR bedpe file. You can use these columns to filter the results based on other criteria, such as method, platform, or study name. Refer to [https://github.com/ncbi/dbvar/tree/master/Structural_Variant_Sets/Nonredundant_Structural_Variants](https://github.com/ncbi/dbvar/tree/master/Structural_Variant_Sets/Nonredundant_Structural_Variants) for the list of columns included in the files.
#### 6. Other options
- Run bedtools with "-f 1" to find variants with 100% reciprocal overlap in NR.
- Run bedtools with "-u" instead of "-wo" to see only unique id's from variant file.  For example:
```markdown
bedtools intersect -a variant_calls.gff -b GRCh37.nr_deletions.bedpe -u -r -f 1 > variant_calls_X_nr_deletions.unique.100pct.gff
more variant_calls_X_nr_deletions.unique.100pct.gff
chr2    dbVar   copy_number_loss        165850456       165864123       .       +       .       ID=chr2_165850456_165864123_copy_number_loss_7

grep chr2_165850456_165864123_copy_number_loss_7 variant_calls_X_nr_deletions.gff
```


----------

### Find overlaps between NR SVs and annotation datasets
This case may be helpful if you would like to know if candidate structural variants overlap other NCBI annotation resources.

#### 1. Format your file or candidate structural variants as either gff, bed, or bedpe. For example:
variant_calls.gff:


```
chr12 dbVar short_tandem_repeat 132387673 132387821 . + . ID=chr12_132387673_132387821_short_tandem_repeat_1
chr5 dbVar alu_insertion 62339523 62339830 . + . ID=chr5_62339523_62339830_alu_insertion_1
chr9 dbVar insertion 137921881 137921881 . + . ID=chr9_137921881_137921881_insertion_7
chr7 dbVar deletion 67715920 67716363 . + . ID=chr7_67715920_67716363_deletion_2
```



#### 2. Download and prepare annotation files
GRCh37:
Download the following:
RefSeq annotations file, which include genes, exons, and regulatory regions: [ftp://ftp.ncbi.nlm.nih.gov/refseq/H_sapiens/H_sapiens/ARCHIVE/ANNOTATION_RELEASE.105/GFF/ref_GRCh37.p13_top_level.gff3.gz](ftp://ftp.ncbi.nlm.nih.gov/refseq/H_sapiens/H_sapiens/ARCHIVE/ANNOTATION_RELEASE.105/GFF/ref_GRCh37.p13_top_level.gff3.gz)

Paralogous alignments: [ftp://ftp.ncbi.nlm.nih.gov/pub/murphyte/PSV/GRCh37.p13_AR105/all.annot.gff3.gz](ftp://ftp.ncbi.nlm.nih.gov/pub/murphyte/PSV/GRCh37.p13_AR105/all.annot.gff3.gz)  

Dosage Sensitivity (more information here: [https://www.ncbi.nlm.nih.gov/dbvar/studies/nstd45/](https://www.ncbi.nlm.nih.gov/dbvar/studies/nstd45/)): [ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/data/Homo_sapiens/by_study/gvf/nstd45.GRCh37.variant_region.gvf.gz](ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/data/Homo_sapiens/by_study/gvf/nstd45.GRCh37.variant_region.gvf.gz)

Combine files and translate the NCBI accessions to chromosome names
```markdown
gunzip ref_GRCh37.p13_top_level.gff3.gz all.annot.gff3.gz nstd45.GRCh37.variant_region.gvf.gz
cat ref_GRCh37.p13_top_level.gff3 all.annot.gff3 nstd45.GRCh37.variant_region.gvf |
grep -v "###" |  grep "^NC_" | sed "s/NC_000001.10/chr1/g" | sed "s/NC_000002.11/chr2/g" | sed "s/NC_000003.11/chr3/g" |
sed "s/NC_000004.11/chr4/g" | sed "s/NC_000005.9/chr5/g" | sed "s/NC_000006.11/chr6/g" | sed "s/NC_000007.13/chr7/g" |
sed "s/NC_000008.10/chr8/g" | sed "s/NC_000009.11/chr9/g" | sed "s/NC_000010.10/chr10/g" | sed "s/NC_000011.9/chr11/g" |
sed "s/NC_000012.11/chr12/g" | sed "s/NC_000013.10/chr13/g" | sed "s/NC_000014.8/chr14/g" | sed "s/NC_000015.9/chr15/g" |
sed "s/NC_000016.9/chr16/g" | sed "s/NC_000017.10/chr17/g" | sed "s/NC_000018.9/chr18/g" | sed "s/NC_000019.9/chr19/g" |
sed "s/NC_000020.10/chr20/g" | sed "s/NC_000021.8/chr21/g" | sed "s/NC_000022.10/chr22/g" | sed "s/NC_000023.10/chrX/g" |
sed "s/NC_000024.9/chrY/g" | sed "s/NC_012920.1/chrMT/g" | sort > annotations_37.gff
```

GRCh38:
Download the following:

RefSeq annotations file, which include genes, exons, and regulatory regions: [ftp://ftp.ncbi.nlm.nih.gov/refseq/H_sapiens/H_sapiens/GFF/ref_GRCh38.p12_top_level.gff3.gz](ftp://ftp.ncbi.nlm.nih.gov/refseq/H_sapiens/H_sapiens/GFF/ref_GRCh38.p12_top_level.gff3.gz)

Assembly anomalies (more information here: [https://www.ncbi.nlm.nih.gov/genome/tools/remap/docs/alignments](https://www.ncbi.nlm.nih.gov/genome/tools/remap/docs/alignments)): [ftp://ftp.ncbi.nlm.nih.gov/pub/remap/Homo_sapiens/current/GCF_000001405.25_GRCh37.p13/GCF_000001405.38_GRCh38.p12/GCF_000001405.25-GCF_000001405.38.gff](ftp://ftp.ncbi.nlm.nih.gov/pub/remap/Homo_sapiens/current/GCF_000001405.25_GRCh37.p13/GCF_000001405.38_GRCh38.p12/GCF_000001405.25-GCF_000001405.38.gff)

Paralogous alignments: [ftp://ftp.ncbi.nlm.nih.gov/pub/murphyte/PSV/GRCh38.p2_AR107/GRCh38.p2_all.align.gff3.gz](ftp://ftp.ncbi.nlm.nih.gov/pub/murphyte/PSV/GRCh38.p2_AR107/GRCh38.p2_all.align.gff3.gz)

Dosage Sensitivity (more information here: [https://www.ncbi.nlm.nih.gov/dbvar/studies/nstd45/](https://www.ncbi.nlm.nih.gov/dbvar/studies/nstd45/)): [ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/data/Homo_sapiens/by_study/gvf/nstd45.GRCh38.variant_region.gvf.gz](ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/data/Homo_sapiens/by_study/gvf/nstd45.GRCh38.variant_region.gvf.gz)

Combine files and translate the NCBI accessions to chromosome names
```markdown
gunzip ref_GRCh38.p12_top_level.gff3.gz GRCh38.p2_all.align.gff3.gz nstd45.GRCh38.variant_region.gvf.gz
cat GCF_000001405.25-GCF_000001405.38.gff ref_GRCh38.p12_top_level.gff3  GRCh38.p2_all.align.gff3 nstd45.GRCh38.variant_region.gvf |
grep -v "###" |  grep "^NC_" | sed "s/NC_000001.11/chr1/g" | sed "s/NC_000002.12/chr2/g" | sed "s/NC_000003.12/chr3/g" |
sed "s/NC_000004.12/chr4/g" | sed "s/NC_000005.10/chr5/g" | sed "s/NC_000006.12/chr6/g" | sed "s/NC_000007.14/chr7/g" |
sed "s/NC_000008.11/chr8/g" | sed "s/NC_000009.12/chr9/g" | sed "s/NC_000010.11/chr10/g" | sed "s/NC_000011.10/chr11/g" |
sed "s/NC_000012.12/chr12/g" | sed "s/NC_000013.11/chr13/g" | sed "s/NC_000014.9/chr14/g" | sed "s/NC_000015.10/chr15/g" |
sed "s/NC_000016.10/chr16/g" | sed "s/NC_000017.11/chr17/g" | sed "s/NC_000018.10/chr18/g" | sed "s/NC_000019.10/chr19/g" |
sed "s/NC_000020.11/chr20/g" | sed "s/NC_000021.9/chr21/g" | sed "s/NC_000022.11/chr22/g" | sed "s/NC_000023.11/chrX/g" |
sed "s/NC_000024.10/chrY/g" | sed "s/NC_012920.1/chrMT/g" | sort > annotations_38.gff
```

#### 3. Run bedtools
This shows how you could identify the overlaps between your candidate structural variants and the downloaded annotation files.
These examples identify overlaps with at least 75% reciprocal overlap, and the output files will contain columns from both the variant and annotation files.
If your data is on GRCh37:
```markdown
bedtools intersect -a variant_calls.gff -b annotations_37.gff  -wo -r -f .75 > variant_calls.gff_X_annotations_37.gff.min75
```
If your data is on GRCh38:
```markdown
bedtools intersect -a variant_calls.gff -b annotations_38.gff  -wo -r -f .75 > variant_calls.gff_X_annotations_38.gff.min75
```

#### 4. Interpret Results
Identify unique variants with >75% reciprocal overlap with GRCh38 annotation files:
```markdown
cut -f 9 variant_calls.gff_X_annotations_38.gff.min75 | sort -u| wc -l
```
Examine the result file. The GFF files used for annotation will contain a rich set of descriptions in the attribute column, for example:
```markdown
cut -f 18 variant_calls.gff_X_annotations_38.gff.min75 | more
ID=rna15957;Parent=gene5140;Dbxref=GeneID:105373346,Genbank:XR_002959474.1;Name=XR_002959474.1;gbkey=
ncRNA;gene=LOC105373346;model_evidence=Supporting evidence includes similarity to: 5 ESTs%2C 20 long
SRA reads%2C and 99%25 coverage of the annotated genomic feature by RNAseq alignments%2C including 4
samples with support for all annotated introns;product=uncharacterized LOC105373346%2C transcript var
iant X25;transcript_id=XR_002959474.1
```

NOTE: For intersections between GFF and GFF files, col 19 will contain the number of overlapping bases.

----------
