# dbVar Human Nonredundant Structural Variants – Duplications

### Work in progress - data subject to change

Documentation updated:  11/27/2019

## Data Summary

<h3>
Duplications</h3>
<table>
<tbody>
<tr>
<th>Type and FTP Directory</th>
<th>GRCh37</th>
<th>GRCh38</th>
<tr>
<td>All</td>
<td>418,648</td>
<td>408,362</td>
</tr>
<tr>
<td>Common</td>
<td>59,576</td>
<td>59,150</td>
</tr>
<tr>
<td>Pathogenic</td>
<td>4,337</td>
<td>4,206</td>
</tr>
<tr>
<td>Somatic</td>
<td>15,103</td>
<td>15,077</td>
</tr>
</tbody>
</table>

All files are available in **bed**, **bedpe**, and **tsv** formats:

[https://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/duplications/](https://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/duplications/#github)

The variant types in the NR "duplications" files are:

 * copy_number_gain
 * copy_number_variation
 * duplication
 * tandem_duplication

## Records in the NR SV duplications files

### Please note:

* The fields type, method, analysis, platform, variant, study, clinical_significance, clinvar_accession, and gene may contain multiple values.
* Each of the values is associated with one or more calls found in the variant field.
* The values in the variant field are "dbVar call accessions".

* Records in the NR SV duplications files contain the following tab-separated fields.

| chr | outermost_start | outermost_stop | variant_count | variant_type | method | analysis | platform | study | variant | clinical_assertion | clinvar_accession


## Example record 1:

chr | outermost_start | outermost_stop | variant_count | variant_type | method | analysis | platform | study | variant | clinical_assertion | clinvar_accession | bin_size
----|-----------------|----------------|---------------|--------------|--------|----------|----------|-------|---------|--------------------|------------------|------
15 | 90243115 | 90477618 | 1 | copy_number_gain | Oligo_aCGH | Probe_signal_intensity | NA | ClinGen_Laboratory-Submitted | nssv13652018 | Uncertain significance | SCV000495160 | medium

### Explanation:

* The non-redundant coordinates for this record in dbVar are chr15, with
an outermost start of 90243115 and outermost stop of 90477618.

* The variant_count of 1 indicates there is only one ssv with an exact match to
the given placement.  This count does not include SVs with a partial match.

* The variant_call_type is "copy_number_gain".

* The method and the analysis indicate how the one variant was evaluated.

* NA indicates the no platform was submitted for this variant.

* ClinGen_Laboratory-Submitted is the study name as found in dbVar.

* The dbVar variant_accession is "nssv13652018".

* The clinical_significance is "Uncertain significance"

* The variant has an accession in ClinVar of SCV000495160

* bin_size = small (length < 50 bp), medium (<1000000), large (>= 1000000). Length = outermost_stop - outermost_start + 1.

* URLs using the study name accession or variant_accession can be created to access the data
in dbVar, e.g.:
https://www.ncbi.nlm.nih.gov/dbvar/?term=ClinGen_Laboratory-Submitted
https://www.ncbi.nlm.nih.gov/dbvar/?term=nssv13652018

* From the latter page you may click on the "Variant Region ID" on the left to see
the variant's region in the NCBI Variation Viewer at:
https://www.ncbi.nlm.nih.gov/dbvar/variants/nsv2769232/

* The SCV accession can be used to find the record in ClinVar by searching on ClinVar's home page:
https://www.ncbi.nlm.nih.gov/clinvar/

## Example record 2:

chr | outermost_start | outermost_stop | variant_count | variant_type | method | analysis | platform | study | variant | clinical_assertion | clinvar_accession | bin_size 
----|-----------------|----------------|---------------|--------------|--------|----------|----------|-------|---------|--------------------|------------------|-----
8 | 75857739 | 75858539 | 2 | duplication;tandem_duplication | Sequencing | Split_read_and_paired-end_mapping;Read_depth_and_paired-end_mapping | Illumina HiSeq X Ten;Illumina HiSeq 2000 | Wong2016;Alsmadi2014 | essv26064592;nssv3988418 |  |  | medium

### Explanation:

* This is a more complicated example duplication NR record containing multiple
variants with multiple types, methods, and analyses from multiple studies, using
multiple platforms.  This record does not contain clinical_significance or a
ClinVar accession.

# Questions or feedback

* Please email dbvar@ncbi.nlm.nih.gov or create an issue on this GitHub page.

# Thanks!

Thanks for your interest in the dbVar human "non-redundant structural variations" (NR SVs)
data files from NCBI.

Please check back for updates soon.
