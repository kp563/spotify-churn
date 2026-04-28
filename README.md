# Spotify-churn
Don't Stop the Music: Spotify Churn Prediction

Built a supervised ML pipeline in R to predict Premium subscriber churn using the Sparkify event-log dataset (225 users, ~286K interaction records). Engineered user-level behavioral features from raw event logs — total songs played, session frequency, average session length, and days since last activity — then compared Logistic Regression and Random Forest classifiers. The recency feature (days_inactive) turned out to be the dominant predictor by a wide margin, pushing ROC-AUC from 0.664 on the baseline model to 0.944 on the enhanced model, with final classification accuracy of 88.9% on the held-out test set.


The hardest lesson from this project: I ran Random Forest before doing real EDA. The model looked good until I checked the confusion matrix and realized it was quietly over-predicting the majority class on a 23% churn-rate dataset. The fix was straightforward — add recency, evaluate with F1 and balanced accuracy, not just overall accuracy — but the mistake taught me to define what "working" means before touching a model, not after. All code, feature engineering logic, and model evaluation outputs are in this repo.
