# iGEM_Odigos

Odigos: An Improved CRISPR-Cas9 Effective Guide RNA Predictor

Abstract: CRISPRi is a powerful tool for modulating gene expression in human cells. By designing a gRNA homologous to the target gene of interest, one can achieve targeted knockdown of the specific gene of interest. However, with current methodologies, one has to screen multiple gRNA sequences for efficient targeting while minimizing off-target effects. We present a prediction model for identifying the best gRNA sequence for efficient gene targeting in human cells. Starting with experimental data from knocking down specific genes using several gRNAs in iPS cells, we leverage machine learning to inform better selection of the gRNA. Our tool will be invaluable for designing gene targeting gRNAs and will reveal underlying biochemical principles governing CRISPR efficiency.

This project contains 
* Training and test data from Dr. Perli's collected results in Shinya Yamanaka's Lab at Gladstone Institues, UCSF
* Source code to train a new model using RT qRT-PCR data with the pioneering code [Horlbeck et al., eLife 2016)](https://elifesciences.org/content/5/e19760)]
* Comparative study of Weissman algorithm score, our own project's scores, and Dr. Perli's efficiency measurements of each guide.
* A tool to generate 10 small guide RNAs using our model and analyzes off-target stringency for genes in host genome.

### Dependencies
* Python v3.8
* Jupyter notebook
* Biopython
* Scipy/Numpy/Pandas
* Scikit-learn
* bxpython (v0.5.0, https://github.com/bxlab/bx-python)
* Pysam
* Plotly

External command line applications required:
* ViennaRNA
* Bowtie (not Bowtie2)

Large genomic data files required:

* Genome sequence as FASTA ([hg19](http://hgdownload.cse.ucsc.edu/goldenPath/hg19/bigZips/))
* FANTOM5 TSS annotation as BED ([TSS_human](http://fantom.gsc.riken.jp/5/datafiles/phase1.3/extra/TSS_classifier/))
* Chromatin data as BigWig ([MNase](https://www.encodeproject.org/files/ENCFF000VNN/), [DNase](https://www.encodeproject.org/files/ENCFF000SVL/), [FAIRE-seq](https://www.encodeproject.org/files/ENCFF000TLU/))