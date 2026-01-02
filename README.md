# Portfolio Repository

This repository contains the research workflow, drafts, and resources.
It is structured to separate data, analysis, manuscripts, and documentation for better organization and reproducibility.

---

## Directory Structure

```
/ (root)
├─ /data/           # datasets (raw, processed, sample, external)
│   ├─ /raw/        # original, unmodified datasets
│   ├─ /processed/  # cleaned and transformed datasets
│   ├─ /sample/     # small subsets / dummy data for demos or testing
│   └─ /external/   # external references or large datasets (not stored directly in the repo)
├─ /notebooks/      # exploratory and analysis notebooks (Quarto / Jupyter)
├─ /src/            # reusable scripts, utilities, and analysis pipelines
├─ /manuscripts/    # drafts of papers, figures, and supplementary materials
├─ /docs/           # documentation and website build
├─ /results/        # outputs generated from analysis: figures, tables, models, etc.
├─ /env/            # environment specifications (environment.yml / requirements.txt)
└─ README.md        # this file
```

---

## Getting Started

To set up and run the repository locally:

1. **Clone the repo**

   ```bash
   git clone https://github.com/lk01sg/portfolio.git
   cd portfolio
   ```

2. **Set up the environment**

   ```bash
   # with conda
   conda env create -f env/environment.yml
   conda activate portfolio

   # or with pip
   pip install -r env/requirements.txt
   ```

3. **Run notebooks / analysis**

   * Exploratory notebooks are located in `/notebooks/`
   * Example workflows: `/notebooks/example_workflow.ipynb`

4. **Build documentation / site**

   ```bash
   # depending on the toolchain, e.g., Quarto or MkDocs
   quarto render docs
   ```

---

## Workflow

* Initial exploration is done in `/notebooks/`; stable components are refactored into `/src/`.
* Raw data goes into `/data/raw/`, processed datasets into `/data/processed/`.
* Outputs such as figures, models, and tables are stored in `/results/`.
* Drafts of papers are stored in `/manuscripts/`.
* Documentation and the public site are built from `/docs/` and published via GitHub Pages:
  👉 [https://lk01sg.github.io/portfolio](https://lk01sg.github.io/portfolio)

---

## Current Status

* 🔧 **In progress**: notebooks, drafts, and workflow refinement
* ✅ **Stable**: folder structure, environment setup, basic documentation
* 📅 **Last updated**: \[update date here]

---

## License & Contact

**License**: MIT License (see `LICENSE` file for details).

For reuse of code, figures, or any other inquiries:
📧 [lk01sg@protonmail.com](mailto:lk01sg@protonmail.com)

---

## Quick Links

* Project site: [https://lk01sg.github.io/portfolio](https://lk01sg.github.io/portfolio)
* Data documentation: `/data/README.md`
* Example notebook workflow: `/notebooks/example_workflow.ipynb`