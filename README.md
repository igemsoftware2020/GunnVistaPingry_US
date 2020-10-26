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

* For Ubuntu 20.0 systems to install the viennarna package we made it available at https://odigoscrispr.s3-us-west-1.amazonaws.com/viennarna_2.4.15-1_amd64.deb


### Recommended HW Configuration:

* Quad Core 16GB RAM, 100GB Storage Ubuntu 20.04 LTS

### Setup:

* To make it easier the large_data_files referenced by our project are made available at url: https://odigoscrispr.s3-us-west-1.amazonaws.com/large_data_files.tgz
* The contents of this zip are mentioned in https://odigoscrispr.s3-us-west-1.amazonaws.com/large_data_files.README

	* Install the required Python module dependencies.
	* Download and extract the project release.
	* Download and extract the large_data_files directory from above url into our source code directory. 
	* If you extracted large_data_files into a seperate folder then please modify LARGE_FILE_DIR definition in notebook files to point that base directory path.


### Running:

* It is recommended to use jupyter notebook server to run our software. This package contains the following notebooks.
	
	* iGEM_CRISPRi_Library_Design.ipynb :  To train the model and create igem_v1_estimator that can be used to score and/or generate guideRnas.
	* iGEM_CRISPRi_sgRna_Score_Comparision.ipynb:  To do the comparative study of scores of guideRnas across Weissman algorithm, iGEM algorithm and lab scores.
	* iGEM_CRISPRi_Gene_Guide_Selector.ipynb:  To generate guides for a gene including offtarget filtering (Currently supports human and can be extended to different hosts)
	
	* We also made the python version of the above notebooks available that can be run in python 3.8 environment once dependencies are installed.
	
	* Walk through of above note books also made available in html extension.
	
	

