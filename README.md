# Movie Recommender

Hybrid movie recommendation engine (content-based + collaborative filtering) with a Streamlit frontend, covering Hollywood and Bollywood catalogs.

## Approach

- **Content-based** — TF-IDF over genre + overview text, cosine similarity between movies
- **Collaborative** — SVD and user-based KNN (Surprise), trained on MovieLens 100K
- **Hybrid** — weighted blend, 60% CF / 40% CBF, with a popularity-based cold-start fallback for new users

## Structure

```
movie-recommender/
├── app.py              # Streamlit frontend and page routing
├── data_loader.py       # loads, cleans, merges datasets
├── cbf_model.py          # content-based filtering (TF-IDF + cosine similarity)
├── cf_model.py            # collaborative filtering (SVD, KNN)
├── hybrid.py               # blended scoring + cold-start fallback
├── evaluate.py              # RMSE, MAE, Precision@5, Recall@5
├── tmdb_5000_movies.csv       # Hollywood dataset
├── bollywood_movies.csv        # Bollywood dataset
└── requirements.txt
```

## Setup

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

## Run

```bash
streamlit run app.py
```

## Features

- Home — curated collections
- Discover / Browse — filter by genre, popularity
- Search — title lookup with similarity-based recommendations
- My List — session-state watchlist
- Model Stats — SVD/KNN evaluation metrics
- Dark mode toggle

## Notes

- First run trains or loads `svd_model.pkl` — expect a longer cold start.
- Datasets are merged into a single corpus at load time; TF-IDF features are built automatically, not precomputed.
- Collaborative filtering requires a valid MovieLens user ID (`1`–`943`).

## Evaluation

`evaluate.py` reports RMSE and MAE for SVD and KNN, plus Precision@5 and Recall@5 for ranking quality.

## Extending

| To do this | Edit |
|---|---|
| Add a new CF or CBF algorithm | `cf_model.py` / `cbf_model.py` |
| Change hybrid weighting or fallback logic | `hybrid.py` |
| Add a UI page or view | `app.py` |
| Add or enrich a dataset | `data_loader.py` |

## License

MIT
