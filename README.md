# Can Sense-Aware Vocabulary Profiles Enhance BERT-Based CEFR Classification?

This repository contains the code and data processing pipelines for the paper *"Can sense-aware vocabulary profiles enhance BERT-based CEFR classification?"*. (reference to appear when published)

## Repository Structure

```
modernbert_CEFR_vocab_sense/
├── data/
│   ├── *.ipynb                  # Notebook(s) for extracting data from the Write & Improve corpus
│   └── CEFR_sense_tagging/
│       └── *.ipynb              # Sense-level CEFR tagging and vocabulary profile computation
├── classification/
│   ├── validation/
│   │   └── *.ipynb              # Validation experiments and hyperparameter tuning
│   └── test/
│       └── *.ipynb              # Final test set evaluation
└── README.md
```

## Data

The learner texts used in this project come from the [Write & Improve Corpus 2024](https://researchdatasets.cambridge.org/datasets/write-and-improve-corpus-2024), a large-scale dataset of learner English writing annotated with CEFR proficiency levels. The corpus must be downloaded separately from Cambridge University Press & Assessment.

> Nicholls, D., Caines, A., & Buttery, P. (2024). *The Write & Improve Corpus 2024*. Cambridge University Press & Assessment. [https://doi.org/10.17863/CAM.112997](https://doi.org/10.17863/CAM.112997)

### CEFR Sense Tagging

The code in `data/CEFR_sense_tagging/` computes the proportion of words at each CEFR level (A1–C2) for every text in the corpus. This approach assigns CEFR levels at the **word sense** level rather than the word form level, producing richer vocabulary profiles.

The sense-tagging methodology is taken from:

> Hu, N., Lu, X., & Hu, R. (2025). *Behavior Research Methods*, 57(8), 226.

## Classification

The `classification/` directory contains all notebooks used for the CEFR text classification experiments:

- **`validation/`** — Notebooks for model validation, including hyperparameter selection and development set evaluation.
- **`test/`** — Notebooks for final evaluation on the held-out test set.

The classifier is built on [ModernBERT](https://huggingface.co/answerdotai/ModernBERT-base), fine-tuned for CEFR level prediction.

## Getting Started

### Requirements

- Python 3.9+
- PyTorch
- Transformers (Hugging Face)
- Jupyter Notebook

### Installation

```bash
git clone https://github.com/cooperchris17/modernbert_CEFR_vocab_sense.git
cd modernbert_CEFR_vocab_sense
pip install -r requirements.txt
```

### Usage

1. **Data preparation** — Run the notebooks in `data/` to extract and preprocess texts from the Write & Improve corpus.
2. **Sense tagging** — Run the notebooks in `data/CEFR_sense_tagging/` to compute CEFR vocabulary profiles for each text.
3. **Classification** — Run the notebooks in `classification/validation/` for development experiments, then `classification/test/` for final evaluation.
