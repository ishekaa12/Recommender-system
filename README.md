# Movie Recommender

A hybrid movie recommendation app built with Streamlit, combining content-based and collaborative filtering to recommend Hollywood and Bollywood films.

## 🚀 Overview

This project provides an interactive web app for movie discovery. It uses:

- **Content-based filtering** with TF-IDF and cosine similarity
- **Collaborative filtering** with Surprise SVD and KNN
- **Hybrid recommendations** that blend both models
- A **Streamlit frontend** with themed UI and multiple browsing modes

## 📦 Key Files

- `app.py` — Streamlit frontend and navigation
- `data_loader.py` — loads, cleans, and merges datasets
- `cbf_model.py` — content-based recommendation logic
- `cf_model.py` — collaborative filtering using MovieLens and Surprise
- `hybrid.py` — hybrid recommendation logic and cold-start fallback
- `evaluate.py` — evaluation metrics for SVD and KNN models
- `tmdb_5000_movies.csv` — Hollywood dataset
- `bollywood_movies.csv` — Bollywood dataset

## ⚙️ Features

- `Home` view with curated movie collections
- `Discover` and `Browse` views for searching by genre and popularity
- `Search` via title lookup with similarity-based recommendations
- `My List` watchlist support using session state
- `Model Stats` page showing evaluation metrics for SVD and KNN
- `Dark Mode` toggle with retro styling

## 📚 Recommendation Models

- **Content-based filtering** (`cbf_model.py`)
  - Builds TF-IDF vectors from movie genres and overview text
  - Computes cosine similarity between movie feature vectors

- **Collaborative filtering** (`cf_model.py`)
  - Uses MovieLens 100K dataset
  - Trains or loads an SVD model and a user-based KNN model

- **Hybrid recommender** (`hybrid.py`)
  - Combines collaborative and content-based scores
  - Uses a weighted blend (60% CF + 40% CBF)
  - Includes a cold-start fallback recommending popular genre movies

- **Evaluation** (`evaluate.py`)
  - Computes RMSE and MAE for SVD and KNN
  - Computes Precision@5 and Recall@5

## 🛠️ Installation

1. Create a Python environment (recommended):

```bash
python -m venv venv
source venv/bin/activate
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

## ▶️ Run the App

From the project root:

```bash
streamlit run app.py
```

Then open the local URL shown by Streamlit in your browser.

## 💡 Notes

- The first run may take longer because the collaborative filtering model trains or loads from `svd_model.pkl`.
- The app merges the two CSV datasets into a single movie corpus and builds TF-IDF features automatically.
- Valid MovieLens user IDs are `1` through `943` for collaborative recommendations.

## 📁 Dataset Sources

- `tmdb_5000_movies.csv` — Hollywood movies dataset
- `bollywood_movies.csv` — Bollywood movies dataset

## 👨‍💻 Development

To extend the app:

- Add new recommendation algorithms in `cf_model.py` or `cbf_model.py`
- Improve the hybrid scoring in `hybrid.py`
- Add new Streamlit sections and pages in `app.py`
- Replace or enrich datasets in `data_loader.py`
