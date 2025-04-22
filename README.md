## Extract, Align, and Concatenate bac120 Proteins to Infer a Phylogenetic Tree

### Dependencies
- **Python 3**
  - [`plotly`](https://plotly.com/python/), [`Bio` (Biopython)](https://biopython.org/), [`jw_utils`](https://github.com/JonWinkelman/jw_utils)
- **[FastTree](http://www.microbesonline.org/fasttree/)**
- **[HMMER](http://hmmer.org/)**

---

### Pipeline Overview

1. **Extract top HMM protein hit** from each proteome, using a significance threshold.  
   - Input: A directory of proteome FASTA files (`<assembly_accession>.faa`)
2. **Align each group of proteins** to the HMM profile used for extraction.
3. **Concatenate all extracted proteins** for each genome into a single amino acid sequence.
   - Columns are filtered:
     - Columns where all amino acids are identical are removed.
     - Columns with >80% gaps are also removed.
4. **Infer a phylogenetic tree** using FastTree (maximum likelihood, unrooted).

---

### Usage

```python
import make_bac120_tree as mbt
from pathlib import Path

# Paths
DATA = Path('./data')

# Directory containing 120 individual HMM profile files (.txt format)
BAC120_PROFILES = DATA / 'bac120_hmm_profiles'

# Directory containing NCBI proteomes (FASTA files)
# Each file should be named like: GCF_002362295.1.faa
PROTEOME_DIR = DATA / 'Proteomes'

# Run the pipeline
mbt.make_bac120_tree(
    BAC120_PROFILES,
    PROTEOME_DIR,
    proteome_suffix='.faa'
)
```





