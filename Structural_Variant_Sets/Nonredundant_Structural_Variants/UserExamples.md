# NR File Usage Examples
## Purpose

The purpose of this tutorial is to demonstrate the ability to display or compute intersections with the dbVar NR files using popular tools and browsers.

## Input Files
### Subject Files
NOTES:
 - FTP files are located at ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/
 - Genome Browsers can access the FTP files by URL.
 - Locally-installed tools will require the files to be downloaded.
 - BED files have 0-based start and 1-based stops.
 - Chromosome names contain "chr".
 - For the UCSC Genome Browser, set a track name and exclude placements on chrMT.

|File Content|File format|FTP directory/ file|Post-Download instructions|
|------------|-----------|--------|--------------------------|
|Non-redundant deletions|.bed|deletions/ GRCh38.nr_deletions.bed.gz|gunzip GRCh38.nr_deletions.bed.gz; echo "track name=\"dbVar NR deletions\" description=\"non-redundant deletions from dbVar\"" > GRCh38.nr_deletions_ucsc.bed; grep -v ^chrMT GRCh38.nr_deletions.bed >> GRCh38.nr_deletions_ucsc.bed|
|Non-redundant duplications|.bed|duplications/ GRCh38.nr_duplications.bed.gz|gunzip GRCh38.nr_duplications.bed.gz|
|Non-redundant insertions|.bed|insertions/ GRCh38.nr_insertions.bed.gz|gunzip GRCh38.nr_insertions.bed.gz|


### Query Files

Download and run instructions to generate these modified files for testing intersections using locally-installed tools, such as **bedtools:**

NOTES:
 - FTP files are located at ftp://ftp.ncbi.nlm.nih.gov
 - clinvar_chr.vcf
   - "chr" in chromosome names for consistency with the .bed files
- genes_chr.gff
   - for simplicity, filter just the genes on finished chromosomes
   - convert chromosome accessions to names for consistency with the .bed files

**NOTE:** these types of modifications may not be necessary depending on the format of your specific input file.

|File Content|File format|FTP directory/ file|Modified File Name|Post-Download instructions|
|------------|-----------|-----------------|------------------|--------------------------|
|Clinical variants|.vcf|/pub/clinvar/vcf_GRCh38/ clinvar.vcf.gz|clinvar_chr.vcf|gunzip clinvar.vcf.gz; grep "^#" clinvar.vcf > clinvar_chr.vcf; grep -v "^#" clinvar.vcf \| sed "s/^/chr/" >> clinvar_chr.vcf|
|Human genes|.gff|/refseq/H_sapiens/H_sapiens/GFF/ ref_GRCh38.p12_top_level.gff3.gz|genes_chr.gff|gunzip ref_GRCh38.p12_top_level.gff3.gz;  grep "^#" ref_GRCh38.p12_top_level.gff3 > genes_chr.gff; cat ref_GRCh38.p12_top_level.gff3 \| awk -F'\t' '$3~/^gene$/' \| grep "^NC_" \| sed "s/NC_000001.11/chr1/g" \| sed "s/NC_000002.12/chr2/g" \| sed "s/NC_000003.12/chr3/g" \| sed "s/NC_000004.12/chr4/g" \| sed "s/NC_000005.10/chr5/g" \| sed "s/NC_000006.12/chr6/g" \| sed "s/NC_000007.14/chr7/g" \| sed "s/NC_000008.11/chr8/g" \| sed "s/NC_000009.12/chr9/g" \| sed "s/NC_000010.11/chr10/g" \| sed "s/NC_000011.10/chr11/g" \| sed "s/NC_000012.12/chr12/g" \| sed "s/NC_000013.11/chr13/g" \| sed "s/NC_000014.9/chr14/g" \| sed "s/NC_000015.10/chr15/g" \| sed "s/NC_000016.10/chr16/g" \| sed "s/NC_000017.11/chr17/g" \| sed "s/NC_000018.10/chr18/g" \| sed "s/NC_000019.10/chr19/g" \| sed "s/NC_000020.11/chr20/g" \| sed "s/NC_000021.9/chr21/g" \| sed "s/NC_000022.11/chr22/g" \| sed "s/NC_000023.11/chrX/g" \| sed "s/NC_000024.10/chrY/g" \| sed "s/NC_012920.1/chrMT/g" >> genes_chr.gff|

## Bedtools
### Compute Intersections
Refer to:
 - <http://bedtools.readthedocs.io/en/latest/content/tools/intersect.html>
 - **Installation Notes** section at end of this document.

To find ClinVar variants that intersect dbVar deletions, run:
    `bedtools intersect -a clinvar_chr.vcf -b GRCh38.nr_deletions.bed -u > clinvar_dbvar_deletions.vcf`

To find genes that intersect dbVar insertions, run:
    `bedtools intersect -a genes_chr.gff -b GRCh38.nr_insertions.bed -u > gene_dbvar_insertions.gff`

**NOTE:**
 - Use the -u option for unique overlaps.

## Galaxy
### Compute Intersections
 - Go to the online Galaxy server: <https://usegalaxy.org/>
 - NOTE: If the server is down select an alternate server from the displayed list.
 - Select **Get Data** from the **Tools** menubar
 - Select **Upload File** from your computer under **Get Data**
 - In the **Download from web or upload from disk** window
   - select **Paste/Fetch data**
   - Paste the FTP URL in the text box, for example: <ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/deletions/GRCh38.nr_deletions.bed.gz>
   - Select **Start**
   - Wait for the file to complete loading
 - In the **Download from web or upload from disk** window
   - Select **Paste/Fetch data**
   - Paste the FTP URL in the text box, for example: <ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/insertions/GRCh38.nr_insertions.bed.gz>
   - Select **Start**
   - Wait for the file to complete loading
   - Select **Close**
 - Both files should now be displayed in the **History** column
 - Select **Operate on Genomic Intervals** from the **Tools** menubar (you may need to scroll down)
 - Select **Intersect** under **Operate on Genomic Intervals**
 - In the **Intersect the intervals of two datasets (Galaxy Version 1.0.0)** window:
   - Select Downloaded file 1 as the First dataset
   - Select Downloaded file 2 as the Second dataset
   - Select **Execute**
 - Wait for the job to complete
 - When the job is complete, a new file will be displayed in the **History** column, named "**Intersect on data ... and data ...**"
 - Click the **Eye** icon on the new intersect results file to view the data
 - The intersection results will be displayed in the center column of page
 - For example:
![Galaxy](../../images/galaxy.PNG?raw=true "Galaxy")

### Compute Intersections (BED and VCF)
 - Select **Get Data** from the **Tools** menubar
 - Select **Upload File from your computer** under **Get Data**
 - In the **Download from web or upload from disk** window
   - Select **Choose local file**
   - Navigate to the clinvar_chr.vcf file or any other local VCF file
   - Select **Start**
   - Wait for the file to complete loading
   - Select **Close**
 - Select **NGC VCF Manipulating** from the **Tools** menubar (you may need to scroll down)
 - Select **VCF-BEDintersect**
 - In the **VCF-BEDintersect: Intersect VCF and BED datasets (Galaxy Version 1.0.0)** window:
   - Select VCF file, for example, clinvar_chr.vcf
   - Select BED file, for example, downloaded GHRCh38.nr_deletions.bed.gz
   - Select **Execute**
 - Wait for the job to complete
 - When the job is complete, a new file will be displayed in the **History** column, named **VCF-BEDintersect:on data ... and data ...**
 - Click the **Eye** icon on the new intersect results file to view the data
 - The intersection results will be displayed in the center column of page
 - For example:
![Galaxy VCF](../../images/galaxy_vcf.PNG?raw=true "Galaxy")


## UCSC Genome Browser
### Browse

 - Open the **UCSC Genome Browser**: <http://genome.ucsc.edu/cgi-bin/hgGateway>
 - Select **GRCh38/hg38** in the **Human Assembly** pull-down
 - Select **Go**
 - Select **Custom Tracks** from the **My Data** menu in the header menu
 - In the **Paste URLs or data** entry form, select **Choose File**
 - Navigate to select your bed file, for example, **GRCh38.nr_deletions_ucsc.bed**
 - Select **Submit**
 - NOTE: file requirements:
   - "track" line containing name and description
   - chr\* chromosome identifiers
   - no chrMT
   - Follow instructions in **Post-Download instructions** to generate valid file.
 - The custom track name should be displayed in the **Manage Custom Tracks** page
 - Select **Genome Browser** from the header menu
 - The custom track should be displayed
 - Right-click on the track to change the display from **dense** to **full**
 - Zoom in or out sufficiently to see the individual variants
 - Example of display:
![UCSC Genome Browser](../../images/ucsc_browser.PNG?raw=true "UCSC Genome Browser")

Add a second track of insertions:
 - Select **Custom Tracks** from the **My Data** menu in the header menu
 - In the **Paste URLs or data** text entry, paste the URL of the NR insertion file: <ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/insertions/GRCh38.nr_insertions.bed.gz>
 - NOTE:
   - there are no chrMT in the insertion file
   - load without a track name
 - The new track should be displayed as "User Track" in the **Manage Custom Tracks** page
 - Select **Genome Browser**  from the header menu
 - Example of display:
![UCSC Genome Browser insertions](../../images/ucsc_browser_ins.PNG?raw=true "UCSC Genome Browser insertions")

### Compute Intersections
 - Select **Table Browser** from the **Tools** menu in the header menu.
 - Select "Custom Tracks" from **group**, if not already displayed.
 - Select the custom track name, for example, **dbVar NR deletions** from **track.**
 - Select **create** next to **intersection.**
 - The next window will be named: **Intersect with** *your track name*, for example: **Intersect with dbVar NR deletions.**
 - Update the parameters, or use the defaults: **Genes and Gene Predictions.**
 - Select **submit** from the **Intersect with ...** window.
 - In the **Table Browser** window,:
   - Select an **output format** or leave as **BED**
   - Enter a name into **output file** (or leave blank to display output in browser)
 - Select **get output**
 - In the **Output ... as BED** window, select **getBED**
 - The output is generated in a file or displayed in the browser.


## NCBI Sequence Viewer
### Browse
 - Open **NCBI Sequence Viewer** for GRCh38, chromosome 1 in browser: <https://www.ncbi.nlm.nih.gov/projects/sviewer/?id=NC_000001>
 - Select **Tracks**
 - In **Configure Page** window, select **Custom Data**
 - In **Data Source** menu, select **URL**
 - In **URL** form, enter:
   - **URL** <ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/deletions/GRCh38.nr_deletions.bed.gz>
   - **Track Name**: dbVar NR deletions
   - Select **Upload**
 - In **URL** form, enter:
   - **URL** <ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/duplications/GRCh38.nr_duplications.bed.gz>
   - **Track Name**: dbVar NR duplications
   - Select **Upload**
 - In **URL** form, enter:
   - **URL** <ftp://ftp.ncbi.nlm.nih.gov/pub/dbVar/sandbox/sv_datasets/nonredundant/insertions/GRCh38.nr_insertions.bed.gz>
   - **Track Name**: dbVar NR insertions
   - Select **Upload**
 - In **URL** form:
   - Select **Configure**
 - All tracks should be displayed.
   - Chromosome 1 top level:
![NCBI Sequence Browser chr1](../../images/NR_sv_chr1.PNG?raw=true "NCBI Sequence Browser chr1")

   - Chromosome 1 zoomed in:
![NCBI Sequence Browser zoom](../../images/NR_sv_chr1_zoom.PNG?raw=true "NCBI Sequence Browser zoomed")

   - Chromosome 1 showing detailed Non-redundant deletions, duplications, and insertions:
![NCBI Sequence Browser detail](../../images/NR_sv_chr1_detail.PNG?raw=true "NCBI Sequence Browser detail")


# Installation Notes (Linux)
## Bedtools
 - Find the latest bedtools directory in github, for example: <https://github.com/arq5x/bedtools2/releases/tag/v2.27.1>
 - Download the \*.tar.gz file
 - Go to the installation directory and run: `make`
 - Add the bin directory to your path, for example:
   `export PATH=/home/bedtools2.27/bin/:$PATH`
