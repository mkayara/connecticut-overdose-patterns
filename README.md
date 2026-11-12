# Connecticut Overdose Patterns

An exploratory collection of notebooks examining Connecticut's accidental drug-related death records. The project brings together descriptive data exploration, drug co-occurrence analysis, and experimental clustering and supervised models.

> **Public-health context:** these records describe deaths and are not a clinical dataset, a measure of an individual's risk, or a tool for identifying people or directing interventions. Model outputs are exploratory and must not be used for decisions about individuals or communities.

## What is included

| Notebook | Focus |
|---|---|
| [`notebooks/01_deaths_data_exploration.ipynb`](notebooks/01_deaths_data_exploration.ipynb) | Data quality, cleaning, demographic and geographic exploration, and descriptive trends in recorded substances |
| [`notebooks/02_drug_pattern_mining.ipynb`](notebooks/02_drug_pattern_mining.ipynb) | Apriori and FP-Growth exploration of co-occurring record attributes |
| [`notebooks/03_cluster_and_model_experiments.ipynb`](notebooks/03_cluster_and_model_experiments.ipynb) | Experimental clustering, classification, and regression workflows |

The modeling notebook reflects collaborative work; this repository does not claim sole authorship of that source analysis.

The notebooks preserve the original analytical approaches while removing saved cell outputs, local identifiers, and machine-specific dataset paths. Results shown in the source materials are therefore not presented as freshly reproduced findings here.

## Data source

The source dataset is the Connecticut [Accidental Drug-Related Deaths](https://data.ct.gov/Health-and-Human-Services/Accidental-Drug-Related-Deaths/rybz-nyjw) public dataset. Download the CSV from the data publisher and check its current documentation, coverage, field definitions, and reuse terms before analysis.

The dataset is not included in this repository. Keep a downloaded copy outside version control and place it at:

```text
data/accidental_drug_related_deaths.csv
```

The notebooks may include specific preprocessing choices that depend on the source schema and available years. Inspect field names and missingness before running; do not assume a newer dataset extract has the same columns or category values.

## Run the notebooks

Google Colab is the simplest environment for the original interactive workflows. Alternatively, create a Python 3.11 environment and install the listed dependencies:

```sh
python -m venv .venv
```

On Windows:

```powershell
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

On macOS or Linux:

```sh
source .venv/bin/activate
python -m pip install -r requirements.txt
```

Run notebooks from the repository root. Each notebook has its own workflow:

1. `01_deaths_data_exploration.ipynb` reads the downloaded source CSV and can save a processed file to `outputs/`.
2. `02_drug_pattern_mining.ipynb` independently explores patterns from the source CSV.
3. `03_cluster_and_model_experiments.ipynb` reads the source CSV and creates its own processed file in `outputs/`.

They do not need to be run as one continuous pipeline.

The modeling notebook includes TensorFlow and density-clustering dependencies, which may be easier to use in a hosted notebook environment than on Windows.

## Outputs and privacy

Downloaded data, generated CSVs, notebook checkpoints, and local environment files are excluded by `.gitignore`. Notebook outputs are intentionally cleared: executed outputs may embed record-level observations, and historical plots and metrics could be mistaken for results regenerated from the current source.

Review the staged file list before committing. Do not add a downloaded dataset, derived records, personal identifiers, credentials, or source reports.

## Interpretation notes

- Observational patterns describe recorded deaths, not population-level rates unless a suitable population denominator is added.
- Co-occurrence rules are associations in the processed records; they do not establish causal relationships.
- Clusters are algorithm-dependent summaries, not naturally occurring or clinically validated groups.
- Classification and regression targets in the exploratory notebook do not establish an individual's overdose risk or predict future deaths.
- The source notebook's modeling choices should be reviewed before reuse, including target construction, feature leakage, geographic encoding, class balance, validation design, and the suitability of each metric.
- Missing data, changed data coverage, and preprocessing decisions can materially affect results.

## License and attribution

No separate project license is declared. Check the source dataset's current terms and seek permission where required before redistributing source-derived content. The local source reports and PDFs are not included.
