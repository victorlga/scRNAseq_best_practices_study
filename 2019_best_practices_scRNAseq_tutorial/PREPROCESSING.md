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

    "Perform QC by finding outlier peaks in the number of genes, the count depth and the fraction of mitochondrial reads. Consider these covariates jointly instead of separately.
    
    Be as permissive of QC thresholding as possible, and revisit QC if downstream clustering cannot be interpreted.
    
    If the distribution of QC covariates differ between samples, QC thresholds should be determined separately for each sample to account for sample quality differences as in Plasschaert et al (2018)."

## Normalization

1. What is normalization in scRNA-seq context?

    "Each count in a count matrix represents the successful capture, reverse transcription and sequencing of a molecule of cellular mRNA (Box 1). Count depths for identical cells can differ due to the variability inherent in each of these steps. Thus, when gene expression is compared between cells based on count data, any difference may have arisen solely due to sampling effects. Normalization addresses this issue by e.g. scaling count data to obtain correct relative gene expression abundances between cells."

2. What is count depth scaling?

    Also known as counts per million (CPM) normalization, it assumes that all cells in the dataset initially contained an equal number (generally, 1M) of mRNA molecules and count depth differences arise only due to sampling. This is the most common normalization method.

3. What is downsampling protocol? (How to properly downsample? How can I stratify?)

    The process of randomly sampling reads or counts from the data to leave all cells with a prespecified number of counts or fewer.


4, What is high-count filtering CPM?



5. What is Scran's normalization method?



6. What are non-linear normalization methods?



7. Why should apply log(x+1)-transformations?

    "Firstly, distances between log-transformed expression values represent log fold changes, which are the canonical way to measure changes in expression. Secondly, log transformation mitigates (but does not remove) the mean–variance relationship in single-cell data (Brennecke et al, 2013). Finally, log transformation reduces the skewness of the data to approximate the assumption of many downstream analysis tools that the data are normally distributed."

8. Normalization pitfalls & recommendations:

    We recommend scran for normalization of non-full-length datasets. An alternative is to evaluate normalization approaches via scone especially for plate-based datasets. Full-length scRNA-seq protocols can be corrected for gene length using bulk methods.
    
    There is no consensus on scaling genes to 0 mean and unit variance. We prefer not to scale gene expression.
    
    Normalized data should be log(x+1)-transformed for use with downstream analysis methods that assume data are normally distributed.

## Data correction and integration

1. What is the most common biological data correction?
    
    To remove the effects of the cell cycle on the transcriptome. A simple linear regression between cell cycle scores and gene expression is often used to remove these effects. The residual between observed gene expression and the predicted gene expression is substrated from the observed gene expression to obtain the corrected gene expression.

2. What are the techinical effects that may need to be corrected?

    The most common technical effects that need to be corrected are batch effects, which are systematic differences in gene expression between samples that are not due to biological differences. These can arise due to differences in sample processing, sequencing or other experimental conditions. Batch effects can be corrected by regressing out the effect of the batch on gene expression. This is often done by including the batch as a covariate in a linear model and subtracting the residual from the observed gene expression.

3. What is the difference between data integration and batch correction?

    "Correcting for batch effects between samples or cells in the same experiment is the classical scenario known as batch correction from bulk RNA-seq. We distinguish this from the integration of data from multiple experiments, which we call data integration."

4. What is dropout? How expression recovery can help?

    Dropout is when a gene is not detected in a cell due to low expression or technical reasons. Expression recovery is the process of imputing the expression of a gene in a cell that did not detect it. This is often done by using the expression of the gene in other cells as a proxy for the expression of the gene in the cell of interest.

5. Data correction and integration pitfalls and recommendations:

    Regress out biological covariates only for trajectory inference and if other biological processes of interest are not masked by the regressed out biological covariate.

    Regress out technical and biological covariates jointly rather than serially.
    
    Plate-based dataset pre-processing may require regressing out counts, normalization via non-linear normalization methods or downsampling.

    We recommend performing batch correction via ComBat when cell type and state compositions between batches are consistent

    Data integration and batch correction should be performed by different methods. Data integration tools may over-correct simple batch effects.

    Users should be cautious of signals found only after expression recovery. Exploratory analysis may be best performed without this step.

## Feature selection, dimensionality reduction and visualization

