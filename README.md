# Eco-798: Constitutional Diffusion and Evolution in the American States

**A text-as-data analysis measuring lexical similarity and ideological diffusion across U.S. state constitutions using NLP and panel regression.**

## Abstract

This thesis examines how the form and substance of U.S. state constitutions vary across time and geographic space. Using a corpus of 113 historical state constitutions, the study applies TF-IDF cosine similarity to measure lexical resemblance and latent Dirichlet allocation (LDA) to measure thematic overlap. The analysis demonstrates that both language and substantive focus diverge as temporal and geographic separation increases. However, two-way fixed-effects models reveal that while state-specific drafting traditions account for a substantial share of constitutional language (form), changes in substantive priorities (substance) are more closely tied to the historical periods in which the constitutions were adopted.

## Repository Structure

```
thesis research/
├── code/
│   ├── notebooks/              # Jupyter notebooks for primary analysis
│   │   ├── Cosine_Similarity.ipynb
│   │   ├── Load_Constitution_Files.ipynb
│   │   ├── Regression_Analysis.ipynb
│   │   └── Topic_Modeling.ipynb
│   ├── cosine_similarity.py    # Python scripts for NLP tasks
│   ├── regression_analysis.py
│   ├── topic_modeling.py
│   └── topic_modeling_unmerged.py
├── CSV files/                  # Processed datasets, matrices & results
│   ├── clean_constitutions.csv
│   ├── regression_ready_data.csv
│   ├── similarity_matrix_full.csv
│   └── ...
├── text files (constitutions)/ # Raw textual corpus of state constitutions
├── background lit/             # Literature review materials and references
```

## Data

- **Source**: The raw constitutional texts are obtained from the National Bureau of Economic Research (NBER)/Maryland State Constitutions Project. 
- **Corpus**: 113 historical state constitutions. The primary unit of observation is a state constitution adopted in a particular year.
- **Preprocessing**: `Cosine_Similarity.ipynb` cleans the texts by converting to lowercase, lemmatizing, and removing punctuation, whitespace, stop words, numerical tokens, and state names to isolate substantively informative words.

*Note: The generated data files (e.g., `clean_constitutions.csv` at ~38MB and `regression_ready_data.csv` at ~14MB) are quite large and may require local generation if not downloaded directly.*

## Methodology

1. **Text Distance / Lexical Similarity**: Uses Term Frequency-Inverse Document Frequency (TF-IDF) weighted cosine similarity to quantify the resemblance in vocabulary (constitutional form) across all unique pairs of constitutions.
2. **Topic Modeling / Thematic Overlap**: Employs Latent Dirichlet Allocation (LDA) with 7 topics to measure similarity in substantive emphasis (constitutional substance). This captures how much two constitutions focus on the same areas (e.g., Judiciary, Infrastructure, Direct Democracy), even if their specific wording differs.
3. **Econometric Modeling**: Analyzes the relationship between similarity outcomes and temporal/geographic distance using:
   - Pooled OLS
   - Log-log OLS (to capture nonlinear elasticities)
   - Two-way state fixed-effects (to isolate temporal associations from persistent state characteristics)

## Key Findings

- **Lexical Divergence**: Northeastern and Southern constitutions show the steepest declines in textual similarity to their founding documents over time, while Midwestern and Western states have maintained more stable trajectories.
- **Thematic Evolution**: State constitutions evolved from an early focus on foundational principles (Judiciary and Legal Frameworks) in the 18th/19th centuries to more administrative subjects (Infrastructure, Direct Democracy, Zoning, Education) in the late 19th and 20th centuries.
- **Drivers of Diffusion**: Time and geographic distance both negatively impact similarity and topic overlap. However, after applying two-way fixed effects, unobserved state-specific drafting traditions explain a significant portion of lexical similarities, while thematic changes remain strongly driven by the historical era of adoption.

## Status

**Status**: Work in progress — ECO 798 Master's Thesis, 2026.
