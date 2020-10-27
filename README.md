# iGEM_Odigos

Odigos: An Improved CRISPR-Cas9 Effective Guide RNA Predictor

Abstract: CRISPRi is a powerful tool for modulating gene expression in human cells. By designing a gRNA homologous to the target gene of interest, one can achieve targeted knockdown of the specific gene of interest. However, with current methodologies, one has to screen multiple gRNA sequences for efficient targeting while minimizing off-target effects. We present a prediction model for identifying the best gRNA sequence for efficient gene targeting in human cells. Starting with experimental data from knocking down specific genes using several gRNAs in iPS cells, we leverage machine learning to inform better selection of the gRNA. Our tool will be invaluable for designing gene targeting gRNAs and will reveal underlying biochemical principles governing CRISPR efficiency.

This project contains 
* Training and test data from Dr. Perli's collected results in Shinya Yamanaka's Lab at Gladstone Institutes, UCSF
* Source code to train a new model using RT qRT-PCR data with the pioneering code [Horlbeck et al., eLife 2016](https://elifesciences.org/content/5/e19760)]
* Comparative study of Weissman algorithm score, our own project's scores, and Dr. Perli's efficiency measurements of each guide.
* A tool to generate 10 small guide RNAs using our model and analyzes off-target stringency for genes in host genome.

### Dependencies
* Python v3.8
* Jupyter notebook
* Biopython
* Scipy/Numpy/Pandas
* Scikit-learn (On Ubuntu sklearn)
* bxpython (v0.5.0, https://github.com/bxlab/bx-python)
* Pysam
* Plotly
* xlrd

External command line applications required:
* ViennaRNA
	* ViennaRNA binary packages for various Operating systems can be downloaded from  https://www.tbi.univie.ac.at/RNA/#binary_packages
	* RNAfold binary from this package is used study secondary structure data.
* Bowtie (not Bowtie2)

Large genomic data files required:

* Genome sequence as FASTA ([hg19](http://hgdownload.cse.ucsc.edu/goldenPath/hg19/bigZips/))
* FANTOM5 TSS annotation as BED ([TSS_human](http://fantom.gsc.riken.jp/5/datafiles/phase1.3/extra/TSS_classifier/))
* Chromatin data as BigWig ([MNase](https://www.encodeproject.org/files/ENCFF000VNN/), [DNase](https://www.encodeproject.org/files/ENCFF000SVL/), [FAIRE-seq](https://www.encodeproject.org/files/ENCFF000TLU/))



### Recommended HW Configuration:

* Quad Core 16GB RAM, 100GB Storage Ubuntu 18.x/20.04 LTS

### Setup:

* To make it easier the large_data_files referenced by our project are made available at url: https://odigoscrispr.s3-accelerate.amazonaws.com/large_data_files.tgz
* Same package is also available at url: https://odigoscrispr.s3-us-west-1.amazonaws.com/large_data_files.tgz

* The contents of this zip are mentioned in https://odigoscrispr.s3-us-west-1.amazonaws.com/large_data_files.README

	* Install the required Python module dependencies.
	* Download and extract this release.
	* Download and extract the large_data_files directory from above url into our source code directory. 
	* If you extracted large_data_files into a seperate folder then please modify LARGE_FILE_DIR definition in notebook files to point to that base directory path.


### Running:

* It is recommended to use jupyter notebook server to run our software. This package contains the following notebooks.
	
	* iGEM_CRISPRi_Library_Design.ipynb :  To train the model and create igem_v1_estimator that can be used to score and/or generate guideRnas.
	* iGEM_CRISPRi_sgRna_Score_Comparision.ipynb:  To do the comparative study of scores of guideRnas across Weissman algorithm, iGEM algorithm and lab scores.
	* iGEM_CRISPRi_Gene_Guide_Selector.ipynb:  To generate guides for a gene including offtarget filtering (Currently supports human and can be extended to different hosts)

* It is required to run iGEM_CRISPRi_Library_Design.ipynb prior running any of the other two.

	* Walk through of above note books also made available with corresponding html extension.
	
### MAC OS X:

* We observed it is easier to setup these packages and run them using Jupyter Notebook in Anaconda NAVIGATOR
* Add bioconda,conda-forge to Anaconda default channel to install some of required packages mentioned above
* On Some Mac systems we observed RNAfold giving an error about missing  libmpfr.4.dylib. 
	*If required install mpfr using "brew install mpfr" and ensure lib libmpfr.4.dylib is accessible to RNAfold binary.
* bowtie can be installed from the following location https://sourceforge.net/projects/bowtie-bio/files/bowtie/1.3.0/bowtie-1.3.0-macos-x86_64.zip/download
		*Please ensure bowtie is add to PATH so that it can be invoked by our modules to run bowtie to do alignment related study.
	
### Limitations:
* These applicatoin is currently not supported on Windows systems because of limitions on support of certain bio modules used by this application.