# CSCE-698 Individual Research

This repository contains notebook-based data preparation and modeling for a permafrost thermal properties study. The project consolidates source datasets from multiple papers, standardizes units and column names, and exports cleaned tables that can be used for downstream statistical modeling.

## Project Scope

The current workflow focuses on four related notebooks:

- `specific_heat_analysis.ipynb`: cleans and standardizes moisture-dependent specific heat observations from multiple literature sources.
- `temperature_specific_heat_analysis.ipynb`: standardizes temperature-dependent specific heat observations.
- `volumetric_heat_capacity_analysis.ipynb`: combines and cleans volumetric heat capacity datasets, including optional candidate rows that can support specific-heat modeling.
- `specific_heat_modeling.ipynb`: builds grouped and within-source models for specific heat prediction, compares transfer vs within-source performance, and exports modeling summaries.

The repository also includes `permafrost_data.csv` and the underlying source files in `data/raw/`.

## Repository Layout

```text
.
├── README.md
├── LICENSE
├── permafrost_data.csv
├── specific_heat_analysis.ipynb
├── specific_heat_modeling.ipynb
├── temperature_specific_heat_analysis.ipynb
├── volumetric_heat_capacity_analysis.ipynb
├── data/
│   ├── raw/
│   ├── cleaned/
│   ├── processed/
│   └── results/
└── permafrost_env/
```

## Workflow

1. Place literature-derived source CSVs in `data/raw/`.
2. Run the three analysis notebooks to clean source-specific datasets and convert units where needed.
3. Export standardized datasets to `data/processed/` for later modeling or analysis.
4. Run `specific_heat_modeling.ipynb` to evaluate grouped and within-source models and write summary outputs.
5. Use `data/cleaned/` and `data/results/` for intermediate combined outputs and derived summaries.

## Data Processing Highlights

- Unit conversions are standardized across notebooks.
- Repeated fields such as water content, bulk density, source, and soil class are normalized into consistent column names.
- The cleaned outputs are structured so that observations from different papers can be compared or merged more easily.

## Output Files

Typical processed outputs include:

- `data/processed/specific_heat_cleaned.csv`
- `data/processed/temperature_specific_heat_cleaned.csv`
- `data/processed/volumetric_cleaned.csv`
- model-ready derivative tables such as `cp_moisture_model_df.csv`, `temperature_cp_model_df.csv`, `cv_model_df.csv`, and `cp_from_cv_candidates_df.csv`
- modeling outputs such as `moisture_primary_model_summary.csv`, `temperature_model_summary.csv`, `transfer_vs_within_source_summary.csv`, and `final_within_source_summary.csv`

## Environment

The notebooks were developed in a local Python environment stored as `permafrost_env/`. Core dependencies used in the notebooks include:

- `pandas`
- `numpy`
- `matplotlib`
- `scikit-learn`
- Jupyter Notebook / IPython

If you recreate the environment manually, install those packages in a Python 3 environment and run the notebooks from the repository root so relative paths like `data/raw` and `data/processed` resolve correctly.

## Notes

- The notebooks are the primary source of project logic in this repository.
- Generated data products under `data/processed/` can be regenerated from the raw inputs by re-running the notebooks.
- The modeling notebook assumes the cleaned/model-ready CSVs have already been produced by the analysis notebooks.
- If additional modeling notebooks are added later, they should follow the same column conventions used by the current cleaned datasets.
