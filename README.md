# How Climate Change Conversations on Twitter Evolved (2006–2019)

CS334 Course Project · Group 23: Maryam, Izzah, Noor

Data cleaning, exploratory analysis, statistical tests and a stance classifier on 15.8 million climate-related tweets (2006–2019). We look at how the volume, topics, tone, stance and geography of the climate conversation changed over time, and whether unusually hot or cold months show up in what people tweet.

## Dataset

The Climate Change Twitter Dataset (Effrosynidis et al., 2022), available on [Kaggle](https://www.kaggle.com/datasets/deffro/the-climate-change-twitter-dataset). It is not included in this repo because of its size.

15,789,411 tweets with 10 columns: `created_at`, `id`, `lng`, `lat`, `topic`, `sentiment`, `stance`, `gender`, `temperature_avg` (temperature anomaly vs the 1951–1980 average), `aggressiveness`.

## Contents

- `Climate_Change_Twitter_EDA_Group23.ipynb`: Checkpoint 3. Loading, data-quality checks, cleaning and exploratory analysis on all 15.8 million tweets.
- `CP4_Inference_and_Model_Group23.ipynb`: Checkpoint 4. Statistical tests and a stance classifier on a 25% random sample (about 3.9 million tweets).
- `figures/`: the charts from the Checkpoint 4 notebook.
- `results_summary.csv`: one row per test with its key result.

## Research questions and methods

| Question | Method (Checkpoint 4) |
|---|---|
| 1. How did the climate conversation change over time? | Logistic regression (aggression by year, raw vs adjusted); Kruskal–Wallis test (sentiment by topic) |
| 2. Are deniers more aggressive than believers? | Logistic regression controlling for topic, year and gender |
| 3. Did political topics grow, and did aggression rise with them? | Logistic regression with a stance × political-topic interaction |
| 4. Does the gender gap in denial hold in every region? | Logistic regression per region |
| 5. Are the same topics linked to denial and aggression in every region? | Spearman rank correlation with p-values |
| 6. Do unusually hot or cold months change what people talk about, and does this differ by stance? | Logistic regression with cluster-robust errors |
| Can a tweet's stance be predicted from its other labels? | Classifiers: baseline vs logistic regression vs random forest |

## How to run

**Google Colab (recommended for Checkpoint 4)**

1. Download `archive.zip` from the Kaggle page above.
2. Open the notebook in Colab (*File → Open notebook → GitHub*, or upload it). Keep the default CPU runtime; a GPU is not used.
3. Upload `archive.zip` in the Files panel, or copy it from Google Drive using the cell in section 2.
4. *Runtime → Run all*. The first run reads the CSV once and saves `sample_25pct.parquet`; the whole notebook takes about 15–20 minutes and needs about 5 GB of RAM.

**On your own computer**

1. Put `archive.zip` in the same folder as the notebooks.
2. `pip install pandas numpy matplotlib scipy statsmodels scikit-learn pyarrow`
3. Open the notebooks in Jupyter or VS Code and run all cells. With 8 GB of RAM or less, set `SAMPLE_FRACTION = 0.10` in section 4 of the Checkpoint 4 notebook.

## Citation

Effrosynidis, D., Karasakalidis, A. I., Sylaios, G., & Arampatzis, A. (2022). The climate change Twitter dataset. *Expert Systems with Applications*, 204, 117541. https://doi.org/10.1016/j.eswa.2022.117541
