# Sentiment Analysis Streamlit App

A Streamlit deployment of the sentiment-analysis project from the provided notebook.

## Model

The deployment uses:

- TF-IDF Vectorizer
- `max_features=3000`
- `min_df=2`
- `max_df=0.95`
- `ngram_range=(1, 2)`
- `sublinear_tf=True`
- Linear SVM (`LinearSVC`)
- 80/20 stratified train-test split
- `random_state=42`

On the uploaded dataset, this recreated TF-IDF + Linear SVM experiment achieved:

- Test Accuracy: 79.86%
- Weighted F1 Score: 0.7752

## Files

```text
app.py
requirements.txt
svm_model.pkl
README.md
```

## Streamlit deployment

1. Create a GitHub repository.
2. Upload `app.py`, `requirements.txt`, `svm_model.pkl`, and `README.md`.
3. Open Streamlit Community Cloud.
4. Choose **New app**.
5. Select the GitHub repository.
6. Set the main file to `app.py`.
7. Click **Deploy**.

## Run locally

```bash
pip install -r requirements.txt
streamlit run app.py
```

## Important

The original uploaded `svm_model.pkl` contained only a `LinearSVC` with 3012 input features. It did not include the TF-IDF vectorizer required to transform new reviews.

For deployment, the supplied `svm_model.pkl` is a complete scikit-learn Pipeline containing:

1. TF-IDF Vectorizer
2. Linear SVM classifier

Therefore the app can directly transform a new review and make a prediction.

## Output

The application predicts:

- Negative
- Neutral
- Positive

The app does not display probability percentages because `LinearSVC` does not provide calibrated class probabilities.

