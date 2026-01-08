# Portfolio Repository

This repository contains my research workflow, analysis notebooks, manuscripts, and documentation. It is structured to separate data, code, manuscripts, experiments, and outputs for better organization and reproducibility.

---

## Directory Structure

```
/ (root)
├─ README.md
├─ .gitignore
│
├─ /admin/
│   └─ /progress-reports/
│
├─ /code/
│   ├─ /notebooks/           # exploratory & analysis (Jupyter/Quarto)
│   ├─ /src/                 # reusable modules & utilities
│   ├─ /scripts/             # standalone scripts (training, preprocessing, etc.)
│   └─ /tests/               # unit tests & integration tests
│
├─ /data/
│   ├─ /raw/                 # original, unmodified datasets
│   ├─ /processed/           # cleaned & transformed datasets
│   ├─ /sample/              # small subsets for demos/testing
│   └─ /external/            # references to external resources
│       ├─ /pretrained-models/
│       ├─ /embeddings/
│       └─ /auxiliary-datasets/
│
├─ /experiments/
│   ├─ /exp001-baseline/
│   ├─ /exp002-improved/
│   └─ /exp003-deeper-network/
│
├─ /literature/
│   ├─ /papers/
│   │   ├─ /immunotherapy/
│   │   ├─ /machine-learning/
│   │   ├─ /metascience/
│   │   └─ /network-biology/
│   ├─ /books/
│   └─ /notes/               # reading notes & summaries
│
├─ /manuscripts/
│   ├─ /sections/            # chapter drafts (intro, methods, etc.)
│   ├─ /figures/             # figures for papers
│   ├─ /tables/              # tables for papers
│   ├─ /submission/
│   └─ /appendix/
│
├─ /presentations/
│   ├─ /2026-01-15-proposal-defense/
│   ├─ /2026-03-20-progress-seminar/
│   ├─ /2026-07-10-conference-cvpr/
│   ├─ /2026-10-05-final-defense/
│   └─ /templates/
│
├─ /results/
│   ├─ /figures/             # generated plots & visualizations
│   ├─ /tables/              # result tables
│   ├─ /models/              # trained model checkpoints
│   └─ /metrics/             # evaluation metrics & logs
│
├─ /docs/                    # documentation & portfolio website
│   └─ /build/               # generated documentation
│
└─ /env/                     # environment specifications
    ├─ environment.yml       # conda environment
    └─ requirements.txt      # pip dependencies
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

   * Exploratory notebooks are located in `/code/notebooks/`
   * Example workflows can be found in the notebooks directory

4. **Build documentation / site**

   ```bash
   # depending on the toolchain, e.g., Quarto or MkDocs
   quarto render docs
   ```

---

## Workflow

* Initial exploration is done in `/code/notebooks/`; stable components are refactored into `/code/src/`.
* Raw data goes into `/data/raw/`, processed datasets into `/data/processed/`.
* Each experiment gets its own folder in `/experiments/` with a descriptive name.
* Outputs such as figures, models, and tables are stored in `/results/`.
* Literature and reading notes are organized in `/literature/`.
* Drafts of papers are stored in `/manuscripts/`.
* Presentations for defenses and conferences are kept in `/presentations/`.
* Administrative documents like progress reports are in `/admin/`.
* Documentation and the public site are built from `/docs/` and published via GitHub Pages:
  👉 [https://lk01sg.github.io/portfolio](https://lk01sg.github.io/portfolio)

---

## Key Directories Explained

### `/code/`
Contains all executable code organized by purpose:
- **notebooks/** - Jupyter/Quarto notebooks for exploration and analysis
- **src/** - Reusable Python modules and utilities
- **scripts/** - Standalone scripts for training, preprocessing, etc.
- **tests/** - Unit tests and integration tests

### `/data/`
Datasets organized by processing stage. See [`/data/README.md`](./data/README.md) for detailed guidelines.

### `/experiments/`
Each experiment has its own folder with configs, logs, and results. Follow the naming convention: `expXXX-description`.

### `/literature/`
Research papers and books organized by topic, plus reading notes.

### `/manuscripts/`
Paper drafts, figures, tables, and submission materials.

### `/presentations/`
Slides and materials for defenses, seminars, and conferences.

### `/results/`
Generated outputs from experiments and analyses.

---

## Current Status

* 🔧 **In progress**: notebooks, drafts, and workflow refinement
* ✅ **Stable**: folder structure, environment setup, basic documentation
* 📅 **Last updated**: January 2026

---

## License & Contact

**License**: MIT License (see `LICENSE` file for details).

For reuse of code, figures, or any other inquiries:
📧 [lk01sg@protonmail.com](mailto:lk01sg@protonmail.com)

---

## Quick Links

* Project site: [https://lk01sg.github.io/portfolio](https://lk01sg.github.io/portfolio)
* Data documentation: [`/data/README.md`](./data/README.md)
* Environment setup: [`/env/environment.yml`](./env/environment.yml)