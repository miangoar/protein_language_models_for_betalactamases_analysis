# protein language models for betalactamases analysis

**🚨🚨🚨 WARNING - Repository under construction - WARNING🚨🚨🚨**

![image](https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/images/ibt.png)


This repository is part of the thesis "*Comparative evaluation of protein language models for betalactamase classification and prediction of their catalytic activity*" that i have defended in order to get my master's degree in Biochemical Sciences. 

The dataset provided as a dataframe consist in ~26,000 betalactamase sequences with cualitative and cuantitative properties as well as the per-protein embeddings derived from seven protein language models. To create this dataset i used two manually curated databases for betalactamases:
1. For sequences: [Beta-lactamase database (BLDB) - structure and function](https://pubmed.ncbi.nlm.nih.gov/28719998/)
2. For functional measurements: [An Integrative Database of β-Lactamase Enzymes: Sequences, Structures, Functions, and Phylogenetic Trees](https://pubmed.ncbi.nlm.nih.gov/30783007/)

The cuantitative properties were generated with the [ProtParam module of bioPython](https://biopython.org/docs/1.76/api/Bio.SeqUtils.ProtParam.html). The cualitative properties were extracted by scrapping the text of the BLDB and complemented with taxonomic annotations generated with [Diamond2 against the Genome Taxonomy DataBase](https://github.com/hbckleikamp/GTDB2DIAMOND).  

Here is a detaled information about each one of the directories of this respository:
* notebooks: a series of juýter notebooks that i used to analyze betalactamase sequences using protein language models.
* data
  - ancestors/
  - bldb/
    - raw
    - mod 
  - bldb2/
    - kinetics
    - mics 
  - lra5/
  - recognized_fams/
  - risso_consA/
  - varG/
* results
  - ancestral_neighborhood
  - distance
  - esmfold
  - kinetics
  - signalp6
  - tables
  - tax
  - dim_redo
  - embeddings
  - filtSeqByLen
  - mics
  - subclass_a
  - tanimoto
  - training
* images: some images for illustration purposes

<p align="center">
  <img src="https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/images/class_a.png" alt="Texto alternativo">
</p>


## Biological properties detected by protein language models   



<p align="center">
  <img src="https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/images/pipe1.png" alt="Texto alternativo">
</p>

| Notebook | Brief descripcion | 
|-----------|-----------| 
| [notebook 1 ](https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/notebooks/01_Create_sequence_dataset.ipynb) | xxx |
| [notebook 1 ]() | xxx |
| [notebook 1 ]() | xxx |
| [notebook 1 ]() | xxx |
| [notebook 1 ]() | xxx |

## Structural and functional analysis between beta lactam antibiotics and beta lactamases   

<p align="center">
  <img src="https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/images/pipe2.png" alt="Texto alternativo">
</p>

| Notebook | Brief descripcion | 
|-----------|-----------| 
| [notebook 1 ](https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/notebooks/01_Create_sequence_dataset.ipynb) | xxx |
| [notebook 1 ]() | xxx |
| [notebook 1 ]() | xxx |
| [notebook 1 ]() | xxx |
| [notebook 1 ]() | xxx |
