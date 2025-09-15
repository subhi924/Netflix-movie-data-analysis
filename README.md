# Netflix-movie-data-analysis
Project Overview

This repository contains a reproducible analysis of Netflix movie data.
Goals:

Clean and explore the dataset (EDA)

Visualize trends (genres, release years, ratings, runtime)

Build simple models (popularity classification / rating prediction)

Provide a reproducible pipeline and notebook for learning or interview demos

Features

Data cleaning and preprocessing scripts

Exploratory Data Analysis (interactive charts & static plots)

Feature engineering for modeling (genre parsing, release-year bins, text features)

Baseline models: classification (popular vs not) and regression (predict rating)

Jupyter notebooks with step-by-step explanation

Docker / requirements for reproducibility

Repository Structure
netflix-movies-analysis/
├─ data/
│  ├─ mynetflixdb.csv                # raw dataset (not committed if large)
│  ├─ processed/
│  │  ├─ df_cleaned.csv
│  │  └─ embeddings.parquet
│
├─ notebooks/
│  ├─ 01_data_overview.ipynb
│  ├─ 02_eda_visualizations.ipynb
│  ├─ 03_feature_engineering.ipynb
│  └─ 04_modeling_and_evaluation.ipynb
│
├─ src/
│  ├─ data_loader.py
│  ├─ cleaning.py
│  ├─ features.py
│  ├─ visualize.py
│  └─ model.py
│
├─ requirements.txt
├─ environment.yml   # optional conda env
├─ Dockerfile        # optional reproducible environment
└─ README.md

Dataset

Expected columns (may vary depending on source):

show_id, title, director, cast, country, date_added, release_year, rating, duration, listed_in (genres), description, vote_average / vote_count / user_rating (if present)

Place your CSV file as data/mynetflixdb.csv. If the file is large, keep raw data outside the repo and use .gitignore.

Quick Start — Local (pip)

Clone the repo:

git clone <repo-url>
cd netflix-movies-analysis


Create venv and install:

python -m venv .venv
source .venv/bin/activate      # mac/linux
.venv\Scripts\activate         # windows
pip install -r requirements.txt


Run notebooks (Jupyter):

jupyter lab
# or
jupyter notebook

Quick Start — Conda (optional)
conda env create -f environment.yml
conda activate netflix-analysis
jupyter lab

Key Notebooks & What They Do

01_data_overview.ipynb — load data, inspect schema, handle encoding issues and parsing problems (tips: engine='python', on_bad_lines='skip', encoding='latin1').

02_eda_visualizations.ipynb — plots:

distribution of release years

top genres by count

runtime vs rating scatter

heatmap of correlations (numerical fields)

top directors / actors

03_feature_engineering.ipynb — generate features:

genre one-hot encoding or multi-hot vectors

release_year buckets (decades)

title/description text features (TF-IDF or embeddings)

popularity label creation (e.g., quartiles of vote_average or vote_count)

04_modeling_and_evaluation.ipynb — model baselines:

classification: Logistic Regression, RandomForest, XGBoost for popularity

regression: Ridge/Lasso, RandomForest for rating prediction

evaluation: accuracy, precision/recall, ROC-AUC, RMSE, R²

cross-validation & hyperparameter tuning
