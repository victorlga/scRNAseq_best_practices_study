# Feature selection, dimensionality reduction and visualization

## Feature selection

1. How to select features?

    The first step is to keep only genes that are informative of the variability in the data. Thus, highly variable genes are often used. Depending on the taks and the complexity of the dataset, typically between 1000 and 5000 HVGs are selected for downstream analysis. "Optimally, HVGs should be selected after technical data correction to avoid selecting genes that are highly variable only due to, e.g., batch effects."

2. What is dimensionality reduction?

    The biological manifold on which cellular expression profiles lie can be sufficiently described by far fewer dimensions than the number of genes. Dimensionality reduction aims to find these dimensions. Main objectives of DR: visualization and summarization. Visualization is describing dataset in 2 or 3 dimensions. Summarization is reducing the dataset to its essential data.

3. How is DR done?

    Linear and non-linear combinations of feature space dimensions. In the non-linear case, interpretability is sacrified. Two popular DR techiniques are principal component analysis (linear) and diffusion maps (non-linear). For vizualization purposes the standart is to use linear DR methods, specifically t-distributed stochastic neighbour embedding (t-SNE), but its exagerate differences between cell-populations and overlook potential connections between these populations. Uniform Approximation and Projection (UMAP) is an alternative, and also great for its speed and scalability.

4. Feature selection pitfalls & recommendations:

    We recommend selecting between 1,000 and 5,000 highly variable genes depending on dataset complexity.

    Feature selection methods that use gene expression means and variances cannot be used when gene expression values have been normalized to zero mean and unit variance, or when residuals from model fitting are used as normalized expression values. Thus, one must consider what pre-processing to perform before selecting HVGs.

    Dimensionality reduction methods should be considered separately for summarization and visualization.

    We recommend UMAP for exploratory visualization; PCA for general purpose summarization; and diffusion maps as an alternative to PCA for trajectory inference summarization.

    PAGA with UMAP is a suitable alternative to visualize particularly complex datasets.

## Visualization

1. How visualization should be done in each preprocessing stage?

    "Use measured data for statistical testing, corrected data for visual comparison of data and reduced data for other downstream analysis based on finding the underlying biological data manifold."

## Downstream analysis

1. What is downstream analysis?

    Methods to extract biological insights and describe the underlying biological system. These descriptions are obtained by fitting interpretable models to the data.

2. How is cell- and gene-level analysis?

    Cell- and gene-level analysis typically focuses on clusters and trajectories. Clusters analysis tries to categorize cells into groups. In trajectory analysis data is regarded as a snapshot of a dynamic process, and it investigate this process.