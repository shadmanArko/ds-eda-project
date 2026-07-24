# King County Housing EDA — Client: Bonnie Brown

An exploratory data analysis (EDA) of King County (Seattle area, USA) home sales, built for a fictional client, **Bonnie Brown** — a seller who owns a typical mid-tier house in a "middle-class" King County zip code and wants to sell within the next 6–12 months for the best possible price.

The project connects to a PostgreSQL database, cleans the raw data, and answers five client-specific hypotheses (plus a broader sanity-check sweep) with the goal of turning the analysis into concrete, non-technical recommendations.

## Client & Scope

- **Client:** Bonnie Brown (seller)
- **Definition of "middle-class":** zip codes whose median sale price falls in the 40th–60th percentile across King County (see the SQL in [`03_fetching_the_data_eda.ipynb`](03_fetching_the_data_eda.ipynb)) — 14 zip codes, 3,818 sales, May 2014–May 2015
- **Assumption:** Bonnie is treated as owning a typical house for her zip code's market, not one specific address — all client-facing conclusions are framed at that market level

## Key Findings (short version — full detail in [`05_eda.ipynb`](05_eda.ipynb))

1. **Location still matters, even within "middle-class."** Median price varies ~28% across the 14 qualifying zip codes (98072 at \$515,000 vs. 98019 at \$401,250).
2. **Construction quality (`grade`) drives price; cosmetic condition doesn't.** Grade correlates strongly with price (ρ ≈ 0.70); condition is essentially uncorrelated (ρ ≈ -0.02).
3. **Living space beats room count.** `sqft_living` (r ≈ 0.71) is a far stronger price driver than bedrooms, bathrooms, or floor count.
4. **A genuine renovation shows a real premium (~21% price/sqft); listing season shows only a small one (~3–4%).**
5. **Waterfront/view access, while rare (~1%), is the single largest price lever found** — worth checking regardless of the other findings.

Full reasoning, caveats, and six client recommendations are in the "Insights & Recommendations" section at the end of [`05_eda.ipynb`](05_eda.ipynb).

## Repository Guide

Work through the numbered files in order — each builds on the previous one.

| File / Folder | Description |
| --- | --- |
| [**01 - Assignment**](01_assignment.md) | The original project brief: dataset, tasks, deliverables, and client list. |
| [**02 - Workflow**](02_workflow.md) | The recommended EDA methodology this project follows. |
| [**03 - Fetching the Data**](03_fetching_the_data_eda.ipynb) | Connects to the PostgreSQL `eda` schema and pulls the "middle-class" subset into a CSV. |
| [**04 - Data Cleaning**](04_data_cleaning.ipynb) | Fixes data types, a real `yr_renovated` data-entry bug, missing values (flagged then imputed/derived), and reviews duplicates/outliers. Produces the cleaned dataset. |
| [**05 - EDA**](05_eda.ipynb) | Data overview → 5 hypotheses (Primary EDA) → remaining-columns sweep (Secondary EDA) → Insights & Recommendations for Bonnie. |
| [**Column Names**](column_names.md) | Data dictionary for the raw King County housing columns. |

### Data & Reports

| File / Folder | Description |
| --- | --- |
| [`data/bonnie_brown_middle_class_houses.csv`](data/) | Raw pull from the database (not tracked in git — see `.gitignore`). |
| [`data/bonnie_brown_middle_class_houses_clean.csv`](data/) | Cleaned dataset produced by `04_data_cleaning.ipynb`; used by `05_eda.ipynb` (not tracked in git). |
| [`reports/bonnie_brown_eda_report.html`](reports/) | Standalone [ydata-profiling](https://github.com/ydataai/ydata-profiling) automated report, generated from the cleaned data as a supplementary sanity check. |
| [`slides/briefing.html`](slides/briefing.html) | Client-facing HTML slide deck — non-technical summary of methodology and recommendations for Bonnie. Open directly in a browser. |
| [`slides/slide_content_draft.md`](slides/slide_content_draft.md) | Planning doc: per-slide content, speaker notes, and timing guide used to build `briefing.html`. |

### Project Configuration

| File / Folder | Description |
| --- | --- |
| [`.env.example`](.env.example) | Template for database credentials. Copy to `.env` and fill in your own values (never commit `.env`). |
| [`pyproject.toml`](pyproject.toml) | Project dependencies (pandas, seaborn, plotly, ydata-profiling, SQLAlchemy, etc.). |
| [`uv.lock`](uv.lock) | Locked dependency versions. |

## Setup

> [!NOTE]
> Text in angle brackets like `<repo-name>` is a placeholder — replace it, including the `< >`, with your own value.

### 1. Clone the Repository

```bash
git clone <copied-ssh-url>
cd <repo-name>
```

### 2. Install Dependencies

This creates a virtual environment in `.venv/` and installs everything from `pyproject.toml` / `uv.lock`.

```bash
uv sync
```

> [!TIP]
> Need a library that isn't installed yet? Add it with `uv add <package-name>` — this updates `pyproject.toml` and `uv.lock` and installs it into `.venv`.

### 3. Set up Database Credentials

```bash
cp .env.example .env
```

Open `.env` and fill in the King County housing database credentials (the same ones used in DBeaver). These feed [`03_fetching_the_data_eda.ipynb`](03_fetching_the_data_eda.ipynb).

> [!CAUTION]
> `.env` holds secrets and must never be committed — it's already in `.gitignore`.

### 4. Run the Notebooks

Open the project folder in VS Code (or PyCharm/Jupyter) so it detects the `uv sync` environment, then run the notebooks **in order**: `03` → `04` → `05`. Each notebook reads the output of the previous one from `data/`.

```bash
code .
```

## References & Further Reading

- [**House Sales in King County dataset**](https://www.kaggle.com/datasets/harlfoxem/housesalesprediction): The source dataset, with column descriptions and community notebooks.
- [**Pandas user guide**](https://pandas.pydata.org/docs/user_guide/index.html): The official guide to data manipulation with pandas.
- [**Seaborn tutorial**](https://seaborn.pydata.org/tutorial.html): Statistical data visualization in Python.
- [**Plotly Express**](https://plotly.com/python/plotly-express/): Interactive charts and maps, used for the geographic visualization.
- [**SQLAlchemy documentation**](https://docs.sqlalchemy.org/en/20/): The database toolkit used to query PostgreSQL from Python.
- [**Hypothesis generation for EDA**](https://www.analyticsvidhya.com/blog/2020/11/an-efficient-way-of-performing-eda-hypothesis-generation/): How to form research questions and hypotheses before diving into the data.
- [**EDA Checklist**](https://github.com/neuefische/datascience-infographics/blob/main/EDA_Checklist.md): A phase-by-phase checklist for working through an exploratory analysis.
- [**Tips for data science presentations**](https://www.dataknowsall.com/storytelling.html): Storytelling techniques for presenting results to a non-technical audience.
