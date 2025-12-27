# 🧵 Predicting Product Ratings from Fashion Reviews
This project presents an end-to-end lifecycle-aware sentiment analysis of Amazon Fashion reviews, investigating whether incorporating product lifecycle context improves transformer-based sentiment classification under severe class imbalance.

Rather than optimising for headline accuracy, the study focuses on class-specific performance, statistical validation, and business-relevant trade-offs—reflecting real-world deployment constraints.

## 🔍 Research Question

To what extent does product lifecycle information contribute to sentiment classification performance, overall and at the class level, in transformer-based NLP models?

## 🛠️ Core Components

The project integrates:

Transformer-based NLP modeling (BERT) using PyTorch and Hugging Face

Lifecycle stage classification with a custom threshold optimisation framework

Class imbalance handling using stratified sampling, focal loss, and class weighting

Ablation studies comparing TF-IDF, BERT-only, and lifecycle-enhanced embeddings

Formal statistical validation (McNemar’s test, confidence intervals, effect sizes)

Visual analytics for communicating performance trade-offs

## 📦 Dataset
- Source: Amazon Fashion Review Dataset
- Size: ~2.5 million reviews
- Features: review text, rating, verified purchase, helpful votes, category, timestamps

## ⭐ Key Features
Lifecycle-Aware Segmentation

Reviews are grouped by product lifecycle stage to capture temporal shifts in customer sentiment.

Class-Imbalance-Aware Modeling

The project prioritises realistic imbalance handling using:

stratified sampling

focal loss

class-weighted optimisation

(Synthetic oversampling was deliberately avoided due to risks of unrealistic text generation.)

Rigorous Model Evaluation

Performance differences are validated using formal hypothesis testing, rather than relying solely on accuracy or F1 scores.

Ablation Studies

Systematic comparison of:

TF-IDF baseline

BERT-only embeddings

BERT + lifecycle embeddings (multiple dimensionalities)

This isolates when lifecycle information contributes meaningful value.

## ⚙️ Model
- **Algorithm**: Random Forest Regressor
- **Target**: Star rating (1.0–5.0)
- **Features**: Sentiment, lifecycle stage, aspect flags, metadata

📓 See full modeling workflow in [FirstProject.ipynb](FirstProject.ipynb)

## 📊 Evaluation
- MAE: **0.81**
- RMSE: **1.19**
- Top predictors: `sentiment_score`, `review_length`
- Feature importance and scatter/residual plots used for interpretation

## 🎨 Visuals
![Feature Importance Chart](images/feature_importance.png)  
![Actual vs Predicted Scatter Plot](images/actual_vs_predicted.png)  
![Prediction Error Distribution](images/error_distribution.png)


##📊 Key Findings

No statistically significant improvement in overall accuracy from lifecycle features

Consistent class-specific gains, particularly in neutral and negative recall, at certain embedding dimensionalities

Lifecycle information appears most valuable in targeted use cases where minority-class detection matters more than aggregate metrics

These findings are interpreted using consumer behaviour theory (Elaboration Likelihood Model and Diffusion of Innovation).


## 🔍 Insights
- Sentiment polarity plays the strongest role in prediction
- Lifecycle and aspect signals show potential but need deeper modeling
- Model is well-calibrated with tight error distribution
  
## 💡 Business Insight

The results demonstrate that:

Model value depends on use case—not headline accuracy.

Lifecycle metadata may be most useful in applications such as:

early dissatisfaction detection

customer risk monitoring

decision-support systems prioritising minority outcomes

## 🔭 Future Work
- Explore XGBoost or Ordinal Regression
- SHAP interpretation for local explainability
- Interaction terms between sentiment and aspects or lifecycle stages

## 🧰 Tech Stack
Python · pandas · scikit-learn · TextBlob · matplotlib · seaborn

## 👩🏾‍💻 About the Author
Project by Yetunde Olajumoke Olaleye  
Current MSc Business Analytics student at the University of Greenwich  
Passionate about NLP, consumer behavior, and data-driven strategy
