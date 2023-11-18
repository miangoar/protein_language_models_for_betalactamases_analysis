### <div align="center">  :construction::construction: REPOSITORY UNDER CONSTRUCTION :construction::construction: </div>

# Comparative evaluation of protein language models for betalactamase classification and prediction of their catalytic activity


![image](https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/images/ibt.png)
<p align="center">
  <img src="https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/images/blas.png" alt="Texto alternativo">
</p>

# Introduction 

Betalactamases are enzymes that confer resistance to betalactam antibiotics. These enzymes have two classification schemes. The functional classification organizes them based on their ability to degrade antibiotics and has been constructed with clinically relevant betalactamases. The molecular classification organizes them based on their sequences and structures and has been constructed using classical bioinformatics tools. Here we evaluated both classification schemes using protein language models. In the first part of the study, we assessed the ability of these algorithms to detect betalactamase groups, along with other properties, to examine the type of information detected. In the second part, we evaluated the ability of protein language models to predict catalytic activity against 21 sets of betalactam antibiotics.

The results of the first part suggest that protein language models like ESM-1b can detect multiple biological signals. The results of the second part suggest that penicillins are more commonly degraded substrates by betalactamases compared to other betalactam antibiotics due to their considerable structural similarity. Additionally, we were able to train a single regressor for Cefoxitin that generates predictions consistent with experiments, making this model a useful tool. To our knowledge, this is the first study that  analyzed the molecular and functional classifications of betalactamases using protein language models and we hope serves as a reference.

This repository is part of my master's thesis in Biochemical Sciences availabe at:  🚨 *PENDING TO BE PUBLISHED* 🚨

Another part of this thesis is [this repository](https://github.com/miangoar/ciencia-de-proteinas-basada-en-IA) with some video lecures, tutorials and other resources in order to promote the use of machine learning approaches in protein science for spanish speakers. The video lectures are mainly aimed to undergrad colleagues. 

[![Ciencia de proteínas basada en IA](https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/images/ia_prot.png)](https://github.com/miangoar/ciencia-de-proteinas-basada-en-IA)

## Workflow (First part): Biological properties detected by protein language models   


In the first part of this thesis i constructed a dataset (provided as a dataframe) that consist in ~26,000 betalactamase sequences with qualitative and quantitative properties as well as their respective per-protein embeddings derived from seven protein language models. 

**Table 1. Cuantitative and cualitative properties derived for betalactamase sequences**
| Properties | Brief description | Type |
|-----------|-----------|-----------|  
| sequence length | the number of residues in a protein | quantitative|
| molecular weight | summatory of the molecular weight (in Daltons) of each of the residues | quantitative| 
| aromaticity | Fraction of amino acids with aromatic properties (F, W, Y) in the sequence |quantitative|
| instability | Protein instability estimated from the frequency of low and high stability dipeptides observed in stable and unstable proteins. Values >40 mean that the protein is unstable (has a short half-life). | quantitative|
| hydropathy (gravy) | It is estimated as the sum of the hydropathy of each residue divided by the length of the sequence. | quantitative|
| entropy | Estimation of the diversity of the sequence composition. Low values mean less diversity of amino acids in the composition. A sequence with minimum entropy is a sequence composed of only one type of residue, while a sequence with maximum entropy has all possible residues in equal proportions. | quantitative|
| isoelectric point | Estimation of the pH at which the protein has no net electrical charge | quantitative|
| secondary structure | Estimates made from the fraction of residues associated with helix (V, I, Y, F, W, L), beta folded (E, M, A, L) and turn (N, P, G, S) regions. | quantitative|
| taxonomy | Annotation at the level of Phylum, Class, Order, Family, Genus and Species against the Genome Taxonomy Database. | qualitative|
| reference sets | Ancestors and consensus sequences. | qualitative|
| molecular classification (Ambler) | Labels corresponding to classes (A, C and D), subclasses (A1, A2, B1, B2, B3. C1, C2), families (290 different) and subfamilies (44 within class D). | qualitative|
|per-protein embeddings from protein language models|ESM familiy: ESM and ESM1-b. <br> ProtTrans familiy: XLNet, Prot-T5-BFD and Prot-T5XL-U50. <br> CNN language model: CARP640M. <br> biLSTM language mode: Bepler| per-protein embeddings|

To create this dataset i used [this manually curated database for betalactamases](https://pubmed.ncbi.nlm.nih.gov/28719998/). The quantitative properties were generated with the [ProtParam module of bioPython](https://biopython.org/docs/1.76/api/Bio.SeqUtils.ProtParam.html). The qualitative properties were extracted by scrapping the text of the BetaLactamaseDataBase and complemented with taxonomic annotations generated with [Diamond2 against the Genome Taxonomy DataBase](https://github.com/hbckleikamp/GTDB2DIAMOND). The next diagram shows general strategy used in order to analyze the betalactamse sequences:  


<p align="center">
  <img src="https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/images/pipe1.png" alt="hooooolaaaaa">
</p>

*A total of 25,809 sequences curated by BLDB were analyzed, this DB recognizes 290 enzymatic families. All sequences that did not map to these families were labeled as "Others." As references, signature sequences were estimated for each (sub)class of beta-lactamases (7 sequences), and sequences from ancestors and a consensus were included (5 sequences). Additionally, 201 sequences from a putative new subclass of metallo-beta-lactamases called VarG and the beta-lactamase LRA-5, which has been suggested as a representative of a putative new subclass A3, were included. For a total of 26,023 sequences, protein-level embeddings were extracted conventionally using seven protein language models. To visualize the derived organization from the embeddings, three dimensionality reduction algorithms were used to create two dimensions in which different qualitative and quantitative properties were mapped. Finally, a random sampling of 100 sequences was performed for each (sub)class, and their embeddings were analyzed using two different distance metrics and k-means to evaluate the detection capability of the beta-lactamase classes.*

The next noteboks contain the code used to perform this analysis. You can use [nbviewer](https://nbviewer.jupyter.org/) to render the notebooks if GitHub can't do it. Also you can open the notebook and replace the "github.com" domain by ["nbsanity.com"] domain.(https://nbsanity.com/)

| Notebook |
|-----------|
| [Create the sequence dataset](https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/notebooks/01_Create_sequence_dataset.ipynb) |
| [Generate per protein embeddings](https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/notebooks/02_Generate_embeddings_from_protein_language_models.ipynb) |
| [dimensionality reduction with PCA](https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/notebooks/03_DimRedu_PCA.ipynb) | 
| [dimensionality reduction with tSNE](https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/notebooks/04_DimRedu_tSNE.ipynb) | 
| [dimensionality reduction with UMAP](https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/notebooks/05_DimRedu_UMAP_and_panels.ipynb) | 

## Second part: Structural and functional analysis between beta lactam antibiotics and beta lactamases   

In the second part of this thesis i constructed a dataset (provided as a dataframe) that consist in 2,383 values of minimum inhibitory concentrations (MICs) of 21 beta lactam antibiotics and their associated betalactamases. The data comes from a  [second manually curated database for betalactamases that contain functional information](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6496087/). 

<p align="center">
  <img src="https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/images/pipe2.png" alt="Texto alternativo">
</p>

*This dataset was merged with the dataset of the first part of my thesis and the MICs values were normalized with a log2 transformation of the fold change values of the effect of the betalactam in the MIC assay. A total ofe [50 betalactam antibiotics curated by this databs](https://pubmed.ncbi.nlm.nih.gov/25475113/) were analyzed using their SMILES in order to calculate the pairwise Tanimoto similarity score between them. This structural data was compared with the functional data derived from the MICs. Finally, a comparison of the performance between the seven protein language models was performed in order to find the best model. With this best model a regression model was trained using the NuSVR regressor in order to predict the resisntece level of all of the betalactamases from the first part of this thesis*

| Notebooks |
|-----------|
| [Create the functional dataset](https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/notebooks/06_Create_functional_datasets.ipynb) |
| [Tanimoto similarity analysis](https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/notebooks/07_SMILES_analysis_Tanimoto.ipynb) | 
| [Functional analysis](https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/notebooks/08_Functional_datasets_analysis.ipynb) | 
| [pending](https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/notebooks/) | 
| [pending ](https://github.com/miangoar/protein_language_models_for_betalactamases_analysis/blob/main/notebooks/) | 


## Content by directories   

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
