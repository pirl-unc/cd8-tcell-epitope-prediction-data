# cd8-tcell-epitope-prediction-data

Data for building predictive models of CD8+ T-cell epitopes, including peptide-MHC binding affinity as well as antigen processing steps captured by mass spectrometry data. Most of this data is copied from the curated training data of [MHCflurry 2.0.1](https://github.com/openvax/mhcflurry). 

## Description of files

* [mhc-sequences/class1_mhc_sequences.csv](https://github.com/iskandr/cd8-tcell-epitope-prediction-data/raw/master/mhc-sequences/class1_mhc_sequences.csv): CSV file containing protein sequences of ~15k Class I MHC alleles. These are primarily human (prefixed by "HLA") but also contain several other species (e.g. mouse, cow, &c). Most of the diversity of Class I MHCs occurs in exons 2 * 3, so some sequences are limited to those regions. The most important columsn are `name` and `seq`. 

* [mhcflurry-training-data/peptide-mhc-binding-affinity.csv](https://github.com/iskandr/cd8-tcell-epitope-prediction-data/blob/master/mhcflurry-training-data/peptide-mhc-binding-affinity.csv): 

* [mhcflurry-training-data/eluted-mhc-ligands-mass-spec.csv](https://github.com/iskandr/cd8-tcell-epitope-prediction-data/blob/master/mhcflurry-training-data/eluted-mhc-ligands-mass-spec.csv): 
