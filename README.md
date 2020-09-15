# cd8-tcell-epitope-prediction-data

Data for building predictive models of CD8+ T-cell epitopes, including peptide-MHC binding affinity as well as antigen processing steps captured by mass spectrometry data. Most of this data is copied from the curated training data of [MHCflurry 2.0.1](https://github.com/openvax/mhcflurry). 

## Description of files

* [mhc-sequences/class1_mhc_sequences.csv](https://github.com/iskandr/cd8-tcell-epitope-prediction-data/raw/master/mhc-sequences/class1_mhc_sequences.csv): CSV file containing protein sequences of ~15k Class I MHC alleles. These are primarily human (prefixed by "HLA") but also contain several other species (e.g. mice, cows, &c). Most of the diversity of Class I MHCs occurs in exons 2 * 3, so some sequences are limited to those regions. The most important columsn are `name` and `seq`. 

* [mhcflurry-training-data/peptide-mhc-binding-affinity.csv](https://github.com/iskandr/cd8-tcell-epitope-prediction-data/blob/master/mhcflurry-training-data/peptide-mhc-binding-affinity.csv): CSV containing ~200k measurements of affinity between short peptides and different MHC proteins. Most of these are for human alleles (prefixed by "HLA-") but ~35k come from other species (primarily mouse MHCs, prefixed by "H-2"). The most important columns are:
    * `allele`: name of MHC allele, e.g. "HLA-A\*02:01"
    * `peptide`: amino acid sequence of peptide
    * `measurement_value`: nM affinity (smaller is better), most often a IC50 (inhibitory concentration). Many predictors convert these to a value between 0 and 1 through the transformation  `1 − log(min(IC50, 50000))/log(50000)`.
    * `measurement_inequality`: One of {`=`, `>`, `<`}. Most often `=` but `<` indicates that the measurement is an upper bound (and a lower bound `>`). 

* [mhcflurry-training-data/eluted-mhc-ligands-mass-spec.csv](https://github.com/iskandr/cd8-tcell-epitope-prediction-data/blob/master/mhcflurry-training-data/eluted-mhc-ligands-mass-spec.csv): Peptides identified bound to MHCs on the surface of cells by immuno-precipitation -> elution -> mass spectrometry. The most important columns are:
    * `peptide`: Amino acid sequence of the identified peptide
    * `format`: "MONOALLELIC" when the profiled cells have a unique MHC and otherwise "MULTIALLELIC"
    * `mhc_class`: One of "I" or "II". For CD8+ T-cell epitope prediction only use "I". 
    * `hla`: MHC allele(s) of the profiled cells
