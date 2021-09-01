# Whaleprep

Arthur Zwaenepoel (2018-2019)

Nextflow pipeline and other utilities for preparing an analysis with Whale.
The pipeline does:

1. Alignment with PRANK
2. MCMC with MrBayes
3. CCD construction aith ALEobserve

The dependencies are nextflow, python3, PRANK, MrBayes and ALEobserve. The 
pipeline is configured to work with SGE cluster environments, and should be 
submitted from the head node.

If you haven't installed the `nextflow` or not familiar with `nextflow`, we recommend a brief tutorial on [nextflow](https://www.nextflow.io/). To install the `nextflow`, try the following command

``
curl -s https://get.nextflow.io | bash
```

To run the pipeline in a virtualenv environment, do

```
virtualenv -p=python3 ENV_whaleprep
source $PATH/ENV_whaleprep/bin/activate
$PATH/nextflow whaleprep.nf --fasta <fastadir> --tools $PATH/whaleprep.py
```

where `fastadir` is directory with multifasta files of protein sequences for all
gene families of interest (one file per family). Optional arguments currently are:

```
--tools         path to whaleprep.py
--out           output directory name
--ngen          number of MCMC generations used in MrBayes
--samplefreq    sample frequency for the MCMC 
--burnin        the number of samples to discard as burn-in in ALEobserve
```

Notes on updates: the `Bio.Alphabet` module is removed from `Biopython 1.78` (September 2020),see the [document](https://biopython.org/wiki/Alphabet), the biopython<=1.77 is now required, please try

```
pip install biopython==1.77
```

