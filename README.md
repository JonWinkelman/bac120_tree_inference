## Extract, align and concatenate bac120 proteins to infer phylogenetic tree

* Dependencies
* Python3
- `plotly`, `Bio`, `jw_utils`
* FastTree
* HMMER tools
1. Extract top HMM protein hit from each proteome if above threshold.
- Fasta proteomes must be in a directory together
2. Align each group of HMM-extracted proteins with the HMM profile used to extract them
3. Concatenate all proteins extracted from each genome into one long AA sequence.
* some filtering done.
* if all AAs in a column are identical, that column is removed
* if > 80% of columns have a gap, that column is removed.
4. Use fastTree to generate unrooted maximum likelihood phylogenetic tree.

Usage:  
```
import make_bac120_tree as mbt
# Paths
DATA            = Path('./data')
# This contains the 120 HMM profiles as individual txt files.
BAC120_PROFILES = DATA / 'bac120_hmm_profiles'
# this is a directory containing ncbi dataset proteomes named  <assembly accession>.faa  e.g. GCF_002362295.1.faa
PROTEOME_DIR    = DATA / 'Proteomes'
 
mbt.make_bac120_tree(BAC120_PROFILES, PROTEOME_DIR, proteome_suffix='.faa', )
```



