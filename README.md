# RNAIntels
Machine learning-based tool for discovering coding and non coding small RNAs in human RNA-seq data.
## Description
Following receiving raw sequence readings from an organism, next is the need to classify them into their functional units–coding or non-coding sequences. Coding RNA sequences are translated into protein, while non-coding RNAs, e.g., small non-coding RNA such as miRNA or siRNA, are not translated into proteins but are essential for many significant biological processes, such as gene regulation and gene expressions. Although several research efforts are geared towards developing computational tools for functional prediction of RNA-seq data, identifying coding and non-coding RNAs from raw RNA-seq data remains a challenging task. Here we present a software tool using machine-learning approaches to classify short, human RNA sequences (in the range of 28 – 51 nucleotides) into coding and non-coding RNAs. In contrast to many existing approaches, RNAIntels neither requires raw RNA-Seq sequences (FASTQ) nor aligning the sequences to a human reference genome, thus reducing complexities issues that made other tools less attractive to users.
## Requirements
#### Hardware Requirements
RNAIntels requires a  functional computer system with a minimum of 4g RAM for efficient encoding of the RNA-seq data.

#### OS Requirements
RNAIntels meet the software portability requirements. The software is not platform dependent and can run on Windows, Linux and MacOs operating systems.

## Dependencies
The code is written in Python 3.9.16 and tested on MacOs and Ubuntu 22.04 with the following libraries installed:

Library | Version
--- | --- 
tensorflow | >=2.10.0
biopython | >=1.78
pandas | >=1.53
matplotlib | >=3.7.1
numpy | >=1.23.5
scikit-learn| >=1.2.2
keras | >=2.10.0
plotly | >=5.9.0
multiprocessing | >=2.6.2.1

### Installing all dependencies
```bash
pip install tensorflow biopython pandas matplotlib numpy scikit-learn plotly multiprocessing
```

## Data
The training data, GRCh38 homo sapiens reference data for building the machine learning model, was retrieved from the ENSEMBL database (www.ensembl.org). The raw dataset contained 207,877 instances of protein-coding sequences and 63,865 instances of non-protein coding sequences. We observed that the raw data was inundated with instances of pseudogenes and overlapping sequences. After cleaning the raw data, we obtained a total of 69,420 protein-coding sequences and 28,225 non-coding sequences. We created a balanced dataset ( lenght <= 60 ) from the cleaned data  as training data for the machine learning operations. 

The validation data, human RNA-seq was received from the Institute for Lung Research, Universities of Giessen. 

## Execution
You can execute RNAIntels by running the following python script. The executable file is saved as RNAIntels.py and the Model as RNAIntelsModel.h5.

```bash
git clone --depth 1 https://github.com/OASarumi/RNAIntels.git
cd RNAIntels

# -t determines the number of used cores, -v enables the verbose mode
python3 RNAIntels.py data/validation_coding_red.txt -t 8 -v
```

## License
This software is lincensed under the [MIT license](https://github.com/OASarumi/RNAIntels/blob/main/LICENSE)
