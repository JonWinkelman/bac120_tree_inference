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



