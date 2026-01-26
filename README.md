# Genomic Variants

This repository focuses on mechanistic interpretability experiments for genomic variant classification using Genomic Foundation Models.
The primary workflow lives in `genomic_variant_mechanistic_interpretability.ipynb`.

## Notebooks (variant mechanistic interpretability)

- `data_download_exploration.ipynb`: step-by-step download and verification for ClinVar, hg38 references used by the notebooks, and other datasets that could also be used in the future.
- `genomic_variant_mechanistic_interpretability.ipynb`: loads data, builds ref/alt contexts, trains the classifier, and runs mechanistic interpretability analyses.

## Quickstart (notebook-first)

1) Setup environment
```bash
git clone https://github.com/bowang-lab/genomic-FM.git
cd genomic-FM

pip install torch==2.2.0 torchvision
pip install -r requirements.txt
```
Optional (recommended for notebooks):
```bash
pip install jupyterlab ipywidgets
```
Optional (if you need the Genomic Foundation Model submodule):
```bash
git submodule update --init --recursive
```

2) Data download
- Open `data_download_exploration.ipynb` and follow the cells (ClinVar + hg38 + auxiliary files).
- Expected paths used by the notebooks:
  - ClinVar VCF: `root/data/clinvar_20240416.vcf`
  - hg38 reference: `root/data/hg38.fa` (the `GenomeSequenceExtractor` will auto-download if missing)
- Optional: use the cached dataset helper if you already use GV-Rep data:
```bash
python download_data.py
```

3) Run the analysis notebook
```bash
jupyter lab
```
Then open and run `genomic_variant_mechanistic_interpretability.ipynb`.

## Hardware

- for dataset download: 30GB of disk space
- a NVIDIA GeForce RTX 4090 was used

## Notes

- Set `HF_HOME` or `TRANSFORMERS_CACHE` if you want to control where model weights are cached.
- GPU is recommended for training; CPU will be slow for the full pipeline.

