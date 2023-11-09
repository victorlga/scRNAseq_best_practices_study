# Clustering

1. What is cluster analysis and how is it done?

    Clusters allow us to group cells based on the simmilarity of their gene expression profiles. Expression profile is defined by distance metrics from dimensionality reduced inputs. They may be done by clustering algorithms (classical unsupervised learning) or by community detection methods. Default method to cluster is Louvain algorithm.

2. What is community detection methods?

    "Community detection methods are graph-partitioning algorithms and thus rely on a graph representation of single-cell data. This graph representation is obtained using a K-Nearest Neighbour approach (KNN graph). Cells are represented as nodes in the graph. Each cell is connected to its K most similar cells, which are typically obtained using Euclidean distances on the PC-reduced expression space."

3. Pitfalls and recommendations:

    We recommend clustering by Louvain community detection on a single-cell KNN graph.

    Clustering does not have to be performed at a single resolution. Subclustering particular cell clusters is a valid approach to focus on more detailed substructures in a dataset.

## Cluster annotation

"On a gene level, clustered data are analysed by finding the gene signatures of each cluster. These so-called marker genes characterize the cluster and are used to annotate it with a meaningful biological label."

Before clustering and annotating clusters, the user must decide which level of annotation detail, and thus which cluster resolution, is of interest.

Recently, automated cluster nnotation has become available.By directly comparing the gene expression profiles of annotated reference clusters to individual cells, tools such as scmap (Kiselevet al, 2018b) or Garnett (preprint: Pliner et al, 2019) can transfer annotations between the reference and the dataset. Thus, these methods can perform annotation and cluster assignment simultaneously, without the need for a data-driven clustering step. As cell type and state compositions differ between experimental conditions (Segerstolpe et al, 2016; Tanay & Regev, 2017), clustering based on reference data should not replace the data-driven approach.

Pitfalls & recommendations:

Do not use marker gene P-values to validate a cell-identity cluster, especially when the detected marker genes do not help to annotate the community. P-values may be inflated.

Note that marker genes for the same cell-identity cluster may differ between datasets purely due to dataset cell type and state compositions.

If relevant reference atlases exist, we recommend using automated cluster annotation combined with data-derived marker-gene-based manual annotation to annotate clusters.

## Compositional analysis

Consider that statistical tests over changes in the proportion of a cell-identity cluster between samples are dependent on one another.