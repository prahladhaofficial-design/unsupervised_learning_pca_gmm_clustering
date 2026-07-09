# Unsupervised Learning with PCA, K-Means, and GMMs

A clustering and dimensionality-reduction project comparing PCA projections, K-Means behavior, and Gaussian Mixture Models.

## Overview

Unsupervised learning is useful when labels are unavailable or expensive. This project studies how lower-dimensional structure and clustering assumptions affect the patterns discovered in data.
The workflow compares hard clustering from K-Means with probabilistic clustering from Gaussian Mixture Models.

## Project Design

- Use PCA to inspect dominant directions of variance.
- Run K-Means to study centroid-based hard clustering.
- Run GMMs to study soft cluster membership and distributional assumptions.
- Document observations in both notebook output and markdown notes.

## Key Capabilities

- PCA projection and eigendecomposition-style analysis.
- K-Means clustering experiments.
- Gaussian Mixture Model experiments with EM-style reasoning.
- Cluster visualization and comparison.
- Technical observations stored in markdown.

## Repository Structure

```text
notebooks/pca_gmm_clustering.ipynb  Main unsupervised learning notebook.
docs/technical-observations-1.md    Technical observations.
requirements.txt                    Python dependencies.
```

## Running Locally

```bash
python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook notebooks/pca_gmm_clustering.ipynb
```

## Results and Artifacts

- Notebook plots for dimensionality reduction and clustering behavior.
- Markdown observations summarizing unsupervised-learning results.
- Side-by-side comparison of hard and probabilistic clustering ideas.

## Reproducibility Notes

- Run PCA before GMM cells when reproducing projected clustering results.
- Keep scaling choices fixed because PCA and GMM are sensitive to feature magnitude.
- Regenerate visualizations after changing component count, covariance type, or cluster count.
- Use likelihood and visual separation together when interpreting GMM quality.

## Detailed Workflow

- Open the notebook and inspect the data preparation cells.
- Run PCA sections to understand variance directions and lower-dimensional projections.
- Run K-Means experiments to observe hard cluster behavior.
- Run GMM experiments to observe probabilistic cluster membership.
- Read the technical observations document after inspecting notebook outputs.

## Implementation Details

- The notebook compares dimensionality reduction and clustering in one workflow.
- PCA is used to make structure more visible and reduce feature complexity.
- K-Means represents clusters with centroids and hard labels.
- GMMs represent clusters probabilistically and can model softer boundaries.
- The markdown notes capture observations that are easier to read outside the notebook.

## Data and Inputs

- Data is loaded and transformed inside the notebook.
- Dimensionality reduction changes the representation used for clustering.
- Feature scaling can affect both PCA and clustering results.
- Additional labeled datasets would allow external validation metrics.

## How To Interpret the Results

- PCA plots should be read as projections, not complete views of all data variation.
- K-Means works best when clusters are compact and roughly centroid-shaped.
- GMMs can express uncertainty in cluster membership.
- Differences between K-Means and GMM results reveal assumptions about cluster shape.

## Limitations and Assumptions

- Notebook execution order matters.
- Unsupervised results can be sensitive to preprocessing and initialization.
- Visual cluster separation in PCA space may not capture all high-dimensional structure.
- Additional metrics would strengthen quantitative comparison.


## Review Guide

Use this checklist when reviewing the repository on GitHub:

- Start with the overview to understand the project objective before opening notebooks or source files.
- Read the repository structure section to identify the main entry point.
- Inspect generated outputs before rerunning experiments; they provide a quick view of the current project state.
- Review scripts and notebooks together when both are present, since notebooks often explain decisions while scripts preserve reusable execution paths.
- Check the limitations section before interpreting results too strongly.
- Use the possible extensions section to understand how the project can grow without changing its core purpose.

## Troubleshooting

Common issues and fixes:

- If imports fail, confirm that the virtual environment is activated and dependencies were installed from `requirements.txt`.
- If a notebook cell fails because a variable is missing, restart the kernel and run the notebook from the first cell.
- If a script cannot find a data file, run it from the repository root unless the README gives a different working directory.
- If plots are not regenerated, check that the output folder exists and that the script has write permission.
- If a package version causes errors, create a fresh environment and reinstall dependencies before debugging the source code.
- If GPU-related packages are unavailable, run CPU-compatible sections first and treat heavier deep-learning experiments separately.

## Development Notes

The repository is organized to be understandable before it is optimized. Most code favors clear structure, visible intermediate steps, and saved artifacts over highly compressed implementations. When extending the project, prefer small changes that keep the original experiment reproducible.

Recommended development practices:

- Keep new data files under `data/`, `datasets/`, or the existing local data folder for that project.
- Keep generated figures under `figures/`, `plots/`, `outputs/`, or `results/` depending on the existing convention.
- Add new experiments as separate scripts or clearly labeled notebook sections.
- Avoid overwriting existing outputs unless the experiment is intentionally being refreshed.
- Document any new dependency in `requirements.txt`.
- Prefer relative paths so the repository works after cloning on another machine.

## Project Status

This repository is prepared as a standalone GitHub project. The current version includes the core implementation, documentation, and available artifacts needed to understand the work. Future improvements can focus on stronger automation, more tests, richer visual summaries, and cleaner packaging where appropriate.

## Possible Extensions

- Add silhouette score and adjusted Rand index when labels are available.
- Export cluster visualizations into a `figures/` directory.
- Compare PCA with t-SNE or UMAP for visualization.
- Add a script runner for non-notebook reproduction.

## Tech Stack

Python, NumPy, Pandas, SciPy, imageio, Matplotlib, Jupyter Notebook.

## Author

Prahladha, IIT Hyderabad
