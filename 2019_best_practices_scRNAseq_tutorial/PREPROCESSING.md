## General

1. What is demultiplexing? (?????????)

    Demultiplexing is the process of sorting the mixed sequencing reads into separate datasets, each corresponding to a specific cellular barcode or sample. This involves identifying and separating reads based on their associated barcodes. It ensures that reads from different cells or samples are correctly assigned to their respective datasets.

2. What are count matrices? (???????? Each row is a gene, each column is a barcode, its value is the number of reads corresponding to that gene in that barcode.)

    Count matrices are matrices that contain the number of reads corresponding to each gene in each cell. They are often used as input for downstream analysis.

## Quality control

1. What is cell quality control?

    Cell quality control is the process of ensuring that all cellular barcodes correspond to viable cells. It is common performed based on three QC covariates: the number of counts per barcode, the number of genes per barcode, and the fraction of counts from mitochondrial genes per barcode. Outliersof these covariates are filtered out by thresholding.

2. What is transcript quality control?

    "In addition to checking the integrity of cells, QC steps must also be performed at the level of transcripts. Raw count matrices often include over 20,000 genes. This number can be drastically reduced by filtering out genes that are not expressed in more than a few cells and are thus not informative of the cellular heterogeneity. A guideline to setting this threshold is to use the minimum cell cluster size that is of interest and leaving some leeway for dropout effects."

4. QC pitfalls & recommendations:

    Perform QC by finding outlier peaks in the number of genes, the count depth and the fraction of mitochondrial reads. Consider these covariates jointly instead of separately.
    
    Be as permissive of QC thresholding as possible, and revisit QC if downstream clustering cannot be interpreted.
    
    If the distribution of QC covariates differ between samples, QC thresholds should be determined separately for each sample to account for sample quality differences as in Plasschaert et al (2018).

## Normalization