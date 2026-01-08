# Data Directory

This folder contains datasets used in the portfolio. The goal is to keep raw data, processed data, small samples for demos, and references to external datasets clearly separated to support reproducible research.

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

* **`raw/`** — Store original files as obtained from data providers or experiments. Do not modify these files in-place. Avoid committing sensitive or private data.

* **`processed/`** — Store cleaned, filtered, or transformed datasets that are ready for analysis. Include a reference to the script or notebook that generated them (typically in `/code/notebooks/` or `/code/scripts/`).

* **`sample/`** — Small, representative subsets of data for quick demos or tests. Ensure these contain no sensitive information if derived from real data. Ideal for testing pipelines without loading full datasets.

* **`external/`** — Metadata or instructions (links, checksums, storage locations) for large datasets that cannot be stored in the repo. This includes:
  - **`pretrained-models/`** — References to pretrained model weights (e.g., BERT, ResNet)
  - **`embeddings/`** — Word embeddings, sentence embeddings (e.g., Word2Vec, GloVe)
  - **`auxiliary-datasets/`** — Supporting datasets too large for the repo

---

## Best practices

* Always record the transformation steps used to produce files in `processed/` (notebooks in `/code/notebooks/` or scripts in `/code/scripts/`).
* Prefer storing provenance metadata alongside datasets (e.g., a small YAML or JSON describing source, date, and transformations).
* Do not commit personally identifiable information (PII) or sensitive data to a public repo. Use external storage and reference it in `external/`.
* Keep sample files small (a few MB) so the repository remains lightweight.
* Use `.gitignore` to exclude large data files from being committed accidentally.
* For machine learning projects, store model checkpoints in `/results/models/` rather than in `/data/`.

---

## Example data workflow

1. Place the downloaded/original dataset in `/data/raw/`.
2. Run cleaning/processing scripts (notebooks in `/code/notebooks/` or scripts in `/code/scripts/`) to create `/data/processed/` files.
3. If needed, create a small demo subset in `/data/sample/` for examples and documentation.
4. For large datasets, add download instructions and checksums in `/data/external/` instead of committing the full data.

Example processing workflow:
```bash
# Run preprocessing script
python code/scripts/preprocess_data.py \
  --input data/raw/dataset.csv \
  --output data/processed/dataset_clean.csv

# Or use a notebook
jupyter notebook code/notebooks/01_data_preprocessing.ipynb
```

---

## Metadata recommendation

For each dataset, consider providing a small metadata file (YAML/JSON/MD) including:

* Dataset name
* Source / license
* Date acquired
* Processing steps (brief description or link to script)
* Basic statistics (rows, columns, notable features)
* Any data quality notes or known issues

Example metadata structure (`dataset_metadata.yml`):

```yaml
name: "Sample Dataset"
source: "https://example.com/data"
license: "CC BY 4.0"
date_acquired: "2026-01-08"
processing_script: "/code/scripts/preprocess_data.py"
rows: 10000
columns: 25
description: "Brief description of the dataset"
quality_notes:
  - "Contains 2% missing values in age column"
  - "Outliers removed using IQR method"
```

---

## External Resources

For datasets stored externally (cloud storage, institutional servers), create a reference file:

**Example: `/data/external/pretrained-models/README.md`**
```markdown
# Pretrained Models

## BERT Base Uncased
- **Source**: https://huggingface.co/bert-base-uncased
- **Size**: 440MB
- **Download**: `wget https://huggingface.co/...`
- **Checksum**: sha256:abc123...

## ResNet-50 ImageNet
- **Source**: PyTorch Model Zoo
- **Size**: 98MB
- **Download**: `torch.hub.load('pytorch/vision', 'resnet50', pretrained=True)`
```

---

## Notes

* Store only non-sensitive data in the repository. Use external storage (cloud storage, institutional servers) if required and reference it in `/external/`.
* Monitor repository size; large binary files negatively affect git performance. Use Git LFS if necessary for files > 100MB.
* Keep documentation up-to-date when adding new datasets.
* Coordinate with `/code/` for processing scripts and `/results/` for outputs.
* For experiment-specific datasets, consider storing them in `/experiments/expXXX-name/data/` if they're only used in that experiment.