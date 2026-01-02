# Data Directory

This folder contains datasets used in the portfolio. The goal is to keep raw data, processed data, small samples for demos, and references to external datasets clearly separated to support reproducible research.

---

## Directory Layout

```
/data/
├─ raw/         # original datasets (unchanged)
├─ processed/   # cleaned and transformed datasets ready for analysis
├─ sample/      # small subsets or dummy datasets for demos and testing
└─ external/    # references and instructions for large external datasets
```

---

## When to use each folder

* `raw/` — store original files as obtained from data providers or experiments. Do not modify these files in-place. Avoid committing sensitive or private data.
* `processed/` — store cleaned, filtered, or transformed datasets that are ready for analysis. Include a reference to the script or notebook that generated them.
* `sample/` — small, representative subsets of data for quick demos or tests. Ensure these contain no sensitive information if derived from real data.
* `external/` — metadata or instructions (links, checksums) for large datasets that cannot be stored in the repo.

---

## Best practices

* Always record the transformation steps used to produce files in `processed/` (notebooks or scripts in `/notebooks/` or `/src/`).
* Prefer storing provenance metadata alongside datasets (e.g., a small YAML or JSON describing source, date, and transformations).
* Do not commit personally identifiable information (PII) or sensitive data to a public repo. Use external storage and reference it in `external/`.
* Keep sample files small (a few MB) so the repository remains lightweight.

---

## Example data workflow

1. Place the downloaded/original dataset in `/data/raw/`.
2. Run cleaning/processing scripts (notebooks in `/notebooks/` or scripts in `/src/`) to create `/data/processed/` files.
3. If needed, create a small demo subset in `/data/sample/` for examples and documentation.
4. For large datasets, add download instructions and checksums in `/data/external/` instead of committing the full data.

---

## Metadata recommendation

For each dataset, provide a small metadata file (YAML/JSON/MD) including:

* dataset name
* source / license
* date acquired
* processing steps (brief)
* basic stats (rows, columns, notable columns)

---

## Notes

* Store only non-sensitive data in the repository. Use external storage if required and reference it.
* Monitor repository size; large binary files negatively affect git performance.
