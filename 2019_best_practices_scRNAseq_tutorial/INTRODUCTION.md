# Steps in single-cell RNA sequence analysis

## 0. Data collection
0.1. Single-cell dissociation
0.2. Single-cell isolation
0.3. Library construction
0.4. Sequencing

## 1. Preprocessing
1.1. Raw data processing
1.2. Count matrices
1.3. Quality control     
1.4. Normalization       
1.5. Data correction     
1.6. Feature selection   
1.7. Visualization

## 2. Downstream analysis
2.1. Clustering
2.2. Marker identification
2.3. Cluster annotation
2.4. Trajectory inference
2.5. Differential expression
2.6. Gene dynamics
2.7. Composition analysis
2.8. Metastable states

# Some important definitions

1. What are doublets or multiplets? And empty droplets?

    Cell isolation errors that result in two or more cells being captured together in a single droplet. These cells are then sequenced together and their transcriptomes are combined. Doublets can be identified by their high number of unique molecular identifiers (UMIs) and high number of genes detected. Empty droplets are droplets that do not contain any cells. They can be identified by their low number of UMIs and low number of genes detected.

2. What is library construction?

    Library construction is the process of converting RNA into a sequencing library. This process involves reverse transcription of RNA into cDNA, addition of sequencing adapters, and amplification of the cDNA.

3. What are cellular barcodes?

    In single-cell RNA sequencing, individual cells are often tagged with unique molecular identifiers (UMIs) or cellular barcodes during library preparation. These barcodes are used to identify the source of each sequencing read. Cells may also be tagged with unique barcodes to distinguish them from one another.