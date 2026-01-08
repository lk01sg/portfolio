# Data Directory

This folder contains datasets organized to support reproducible analytical workflows. The structure emphasizes clear data provenance, explicit documentation of transformations, and careful separation of raw materials from processed outputs.

---

## Directory Layout

```
/data/
├─ /raw/                 # original datasets (unchanged)
├─ /processed/           # cleaned and transformed datasets ready for analysis
├─ /sample/              # small subsets or dummy datasets for demos and testing
├─ /external/            # references and instructions for large external datasets
│   ├─ /pretrained-models/
│   ├─ /embeddings/
│   └─ /auxiliary-datasets/
└─ README.md             # this file
```

---

## When to use each folder

* **`raw/`** — Store original files as obtained from data providers, experiments, or databases. These files should remain unmodified to preserve data provenance. Do not commit sensitive or personally identifiable information.

* **`processed/`** — Store cleaned, filtered, or transformed datasets ready for analysis. Each processed file should reference the script or notebook that generated it (typically in `/code/notebooks/` or `/code/scripts/`), including explicit documentation of transformation assumptions and limitations.

* **`sample/`** — Small, representative subsets of data for testing pipelines, demonstrations, or exploratory work without loading full datasets. Ensure these contain no sensitive information if derived from real data. Useful for validating analytical methods before scaling.

* **`external/`** — Metadata, instructions, and references (links, checksums, storage locations) for large datasets that cannot be stored directly in the repository. This includes:
  - **`pretrained-models/`** — References to pretrained model weights (e.g., BERT, ResNet, domain-specific models)
  - **`embeddings/`** — Molecular fingerprints, word embeddings, protein embeddings (e.g., ProtBERT, ESM)
  - **`auxiliary-datasets/`** — Supporting datasets such as pathway databases, interaction networks, or reference annotations

---

## Principles for data management

* **Explicit provenance**: Always document the origin, acquisition date, and transformation pipeline for each dataset
* **Transformation transparency**: Record all processing steps with clear references to the generating code
* **Assumption documentation**: Note data quality issues, filtering decisions, and modeling assumptions that affect downstream interpretation
* **Separation of concerns**: Keep raw data immutable; all transformations should produce new files in `processed/`
* **Reproducibility**: Use version-controlled scripts for all data transformations; avoid manual editing of data files

---

## Example data workflow

1. Place the downloaded/original dataset in `/data/raw/` without modification.
2. Document the source, license, and acquisition context in a metadata file.
3. Run cleaning/processing scripts (in `/code/notebooks/` or `/code/scripts/`) to create files in `/data/processed/`.
4. Document transformation assumptions, data quality decisions, and limitations.
5. For large datasets, add download instructions and checksums in `/data/external/` instead of committing the full data.
6. Create small demo subsets in `/data/sample/` if needed for testing or documentation.

Example processing workflow:
```bash
# Run preprocessing script with explicit parameters
python code/scripts/preprocess_data.py \
  --input data/raw/dataset.csv \
  --output data/processed/dataset_clean.csv \
  --config configs/preprocessing_config.yaml

# Or use a documented notebook
jupyter notebook code/notebooks/01_data_preprocessing.ipynb
```

---

## Metadata recommendation

For each dataset, provide a metadata file (YAML/JSON/MD) documenting:

* Dataset name and description
* Source, license, and citation information
* Date acquired and version (if applicable)
* Processing steps with references to generating scripts
* Data quality assessments and known limitations
* Basic statistics (rows, columns, missing values, distributions)
* Modeling assumptions or constraints relevant to downstream analysis

Example metadata structure (`dataset_metadata.yml`):

```yaml
name: "Sample Biological Dataset"
source: "https://example.org/database"
license: "CC BY 4.0"
citation: "Author et al. (2025). Journal Name."
date_acquired: "2026-01-08"
version: "v2.1"

processing:
  script: "/code/scripts/preprocess_biological_data.py"
  date_processed: "2026-01-09"
  steps:
    - "Filtered samples with <80% assay quality"
    - "Log-transformed expression values"
    - "Removed batch effects using ComBat"
  assumptions:
    - "Assumes normal distribution after log transformation"
    - "Batch correction may reduce biological signal in rare cell types"

statistics:
  samples: 1250
  features: 18500
  missing_rate: 0.02
  outliers_removed: 15

quality_notes:
  - "2% missing values imputed using median"
  - "Outliers defined as >3 SD from mean"
  - "Potential batch confounding in samples 500-600"

limitations:
  - "Small sample size for rare subtypes"
  - "Single time point; no temporal dynamics"
  - "Limited to specific tissue type"
```

---

## External Resources

For datasets stored externally (cloud storage, institutional servers, public repositories), create reference documentation:

**Example: `/data/external/pretrained-models/README.md`**
```markdown
# Pretrained Models

## BERT Base Uncased
- **Source**: https://huggingface.co/bert-base-uncased
- **Purpose**: Text embedding for literature mining
- **Size**: 440MB
- **Download**: `transformers.AutoModel.from_pretrained('bert-base-uncased')`
- **Checksum**: sha256:abc123...
- **License**: Apache 2.0

## ProtBERT
- **Source**: https://huggingface.co/Rostlab/prot_bert
- **Purpose**: Protein sequence embeddings
- **Size**: 1.6GB
- **Download**: See documentation in `/code/scripts/download_protbert.py`
- **Citation**: Elnaggar et al. (2021)
```

**Example: `/data/external/auxiliary-datasets/README.md`**
```markdown
# Auxiliary Datasets

## KEGG Pathway Database
- **Source**: https://www.genome.jp/kegg/
- **Type**: Biological pathway annotations
- **Access**: API-based retrieval (see `/code/scripts/fetch_kegg.py`)
- **License**: Academic use only
- **Last updated**: 2025-12

## STRING Protein Interactions
- **Source**: https://string-db.org/
- **Version**: v11.5
- **Size**: 2.3GB (full network)
- **Download instructions**: `/code/scripts/download_string.sh`
```

---

## Best practices

* **Sensitive data**: Store only non-sensitive data in the repository. Use institutional storage with appropriate access controls for any data containing PII, patient information, or proprietary content. Reference external locations in `/external/`.

* **Repository size**: Monitor repository size carefully. Large binary files degrade git performance. Use Git LFS for files > 100MB, or prefer external storage with documentation here.

* **Data quality**: Document data quality issues explicitly. Transparent reporting of limitations, missing data patterns, and potential biases is essential for sound interpretation.

* **Coordination**: Data processing should coordinate with `/code/` for transformation scripts and `/results/` for analytical outputs. For experiment-specific datasets used only in one analysis, consider storing them in `/experiments/expXXX-name/data/`.

* **Updates**: Keep documentation current when adding new datasets. Update metadata files when reprocessing data or discovering new quality issues.

---

## Notes on interpretation

This data directory emphasizes transparency about data provenance, transformation decisions, and limitations. The goal is to support careful interpretation of analytical results by maintaining clear documentation of assumptions and constraints introduced at the data preparation stage.

For questions about specific datasets or data quality considerations:
📧 [lk01sg@protonmail.com](mailto:lk01sg@protonmail.com)