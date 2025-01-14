## Download data

[Download slice 51/123 Stereo-seq data](https://example.com)

[Download all slices Stereo-seq data and snRNA-seq data](https://example.com)

## Data Description

### spatial transcriptome
In this dataset, the mouse brain was coronally sectioned from anterior to posterior. Stereo-seq libraries were constructed for each coronal section, and spatial transcriptomic sequencing was performed. The spatial locations of individual cells were determined using the StereoCell method (https://github.com/BGIResearch/StereoCell). This database employed a graph convolution network (GCN)-based method, known as Spatial-ID (https://www.nature.com/articles/s41467-022-35288-0), to annotate cell types defined from single-nucleus RNA sequencing data onto cells sequenced with Stereo-seq. This process involved transferring cell types from all 308 cell clusters to high-quality cells across 195 coronal sections (123 for mouse1 and 72 for mouse2), resulting in the creation of a high-resolution cell type annotation atlas of the mouse brain.

"total_gene_T*.txt.gz" file provides the gene expression and spatial position for each stereoseq DNA Nanoball (DNB) on each slice (section).
~~~shell
#eg: 
$less total_gene_T311_mouse_f001_2D_mouse1-20230119.txt.gz | head
gene    x       y       umi_count       cell_label      gene_area       rx      ry
Cavin3  16852   3       1       0       0       13110   17780
Rps18   18302   6       1       0       0       14532   17496
Atp6v1b2        18302   6       1       0       0       14532   17496
Mast3   18302   6       1       0       0       14532   17496
Kcns2   4553    0       1       0       0       1046    20172
Eef2    11235   0       1       0       0       7600    18874
Aprt    15155   0       1       0       0       11446   18113
Utp14b  20942   9       1       0       0       17121   16980
Hsp90aa1        5752    8       1       0       0       2220    19931
#gene: mouse gene name.
#x, y: the original DNB coordinates.
#rx, ry: the DNB coordinates after rotation, which makes the orientation of each section consistent.
#umi_count: non-duplicated reads count.
#cell_label: labeled cell_id by StereoCell method, while 0 stands for DNBs out of cell boundaries.
#gene_area: the region id, and you can find its corresponding region name in "regions-mouse*.tsv" file.
~~~
[Download region description file](https://example.com)

"[stereoseq.celltypeTransfer.2mice.all.tsv.gz](https://example.com)" file provides the cell type annotation of high-quality cells in stereoseq data.
~~~shell
#eg:
$less stereoseq.celltypeTransfer.2mice.all.tsv.gz | head
mouse   section_id      cell_id cell_cluster    cell_subclass   cell_class      color
mouse2  T167    38      VLMC_268        Vascular and leptomeningeal cells       Vascular cells  #8C7456
mouse2  T167    40      EPC_284 Ependymal cells Ventricular cells       #C87EF6
mouse2  T167    44      VLMC_269        Vascular and leptomeningeal cells       Vascular cells  #8D7558
mouse2  T167    47      OL_294  Oligodendrocytes        Oligodendrocytes        #A8E5ED
mouse2  T167    50      MGL_289 Microglia       Microglia       #5858E0
mouse2  T167    54      MGL_289 Microglia       Microglia       #5858E0
mouse2  T167    55      VLMC_268        Vascular and leptomeningeal cells       Vascular cells  #8C7456
mouse2  T167    56      ASC_282 Astrocytes      Astrocytes and olfactory ensheathing cells      #7A944D
mouse2  T167    57      OL_294  Oligodendrocytes        Oligodendrocytes        #A8E5ED
#mouse: the mouse id.
#section_id: original section ID we used in this whole dataset.
#cell_cluster, cell_subclass, cell_class: the cell annotation, transfered from snRNAseq data by Spatial-ID.
#color: colors for plot.
~~~

"[section_id_used_in_paper.tsv](https://example.com)" file provides the conversion of section ids. For the convenience of narration, the article changes the ID of the first section to 'T1' when describing the sections. Here, we provide the correspondence for this transformation. It's important to note that all section IDs recorded in this dataset are the original IDs. If you need to correspond them with the IDs mentioned in the article, please use this table.
~~~shell
#eg:
$head section_id_used_in_paper.tsv
section_id	section_id_used_in_paper
T239	T1
T240	T2
T241	T3
T242	T4
T243	T5
T244	T6
T245	T7
T246	T8
T247	T9
#section_id: original section ID we used in this whole dataset.
#section_id_used_in_paper: section ID we used in the citated article.
~~~

### single nucleus transcriptome
This dataset was generated using single-nucleus RNA sequencing technology. Samples were collected from various regions of the mouse brain, the olfactory bulb, cortex, hippocampus, cerebral nuclei, thalamus, hypothalamus, midbrain, pons, medulla, and cerebellum. Samples were dissected from male mice at 7 weeks. After filtering, we obtained a total of 378,287 high-quality nuclei. Further iterative clustering and classification resulted in 19 cell subclasses and 308 cell clusters. These 19 cell subclasses include telencephalon excitatory neurons, dentate gyrus granule neurons, telencephalon inhibitory neurons, olfactory bulb excitatory neurons, olfactory bulb inhibitory neurons, di-mesencephalon neurons, cholinergic/monoaminergic/peptidergic neurons, rhombencephalon neurons, cerebral nuclei neuroblasts, vascular and leptomeningeal cells, endothelial cells, astrocytes, olfactory ensheathing cells, ependymal cells, hypendymal cells, choroid plexus epithelial cells, microglia, oligodendrocytes, and oligodendrocyte precursor cells.

We provided the raw counts matrix of the single-nucleus RNA data in a Seurat object "mouseBrain.snRNAseq.308Clusters.seurat.20241021.rds", along with the metadata information of the libraries, sample regions, and cell types. We provided a summarized cell types table "mouseBrain.snRNAseq.308ClustersAnnotation.20241021.tsv", which recorded the hierarchical classification of 308 cell clusters.

## **Copyright & License**

To respect the intellectual property rights, protect the rights of data authors, expand services of the data center, and evaluate the application potential of data, data users should clearly indicate the source of the data and the author of the data in the research results generated by using the data (including published papers, articles, data products, and unpublished research reports, data products and other results). For re-posting (second or multiple releases) data, the author must also indicate the source of the original data.

Example of acknowledgement statement is included below: The dataset is provided by Brain Science Data Center, Chinese Academy of Sciences (https://braindatacenter.cn/).
