# CyberBullying_Dissertation


# Evaluating Machine Learning Models for Multi-Class Cyberbullying Detection
# Author Name : Vijaya Ramaraju Chimata 
# Student id : 35056517 
### Project Overview

This project evaluates Machine Learning (ML) models for **six-class cyberbullying classification** using social-media text. The research combines Natural Language Processing (NLP), Term Frequency–Inverse Document Frequency (TF-IDF), model evaluation, Hyperparameter Optimisation (HPO), SHAP explainability, prototype development and human evaluation.

The project addresses the problem of reliably distinguishing different categories of cyberbullying rather than treating the task only as binary cyberbullying detection.

###  Research Question

> How effectively can Machine Learning (ML) models classify multiple categories of cyberbullying in social media text through model evaluation, optimisation, explainability, prototype classification and human evaluation?

###  Aim

The main aim of the dissertation is to evaluate ML models for multi-class cyberbullying detection using NLP and multiple evaluation metrics, optimise the models, identify and explain the best-performing model, and develop a prototype for text classification and human evaluation.

###  Objectives

1. Preprocess and analyse the selected social-media dataset using NLP for multi-class cyberbullying classification.
2. Apply TF-IDF feature extraction and evaluate selected ML models using multiple performance metrics.
3. Optimise the selected models and determine the best-performing model.
4. Apply SHAP to the best-performing model to identify and interpret influential textual features.
5. Develop a functional prototype for categorising user-provided social-media text and conduct human evaluation of usability, functionality and user experience.

###  Dataset

The project uses the publicly available **Cyberbullying Classification** dataset from Kaggle.

**Dataset:** https://www.kaggle.com/datasets/andrewmvd/cyberbullying-classification/data

The dissertation describes the dataset as containing approximately **47,000 tweets across six balanced categories**:

- Age
- Ethnicity
- Gender
- Religion
- Other cyberbullying
- Not cyberbullying

**Dataset reference:**

Andrewmvd. (2020). *Cyberbullying classification* [Dataset]. Kaggle. https://www.kaggle.com/datasets/andrewmvd/cyberbullying-classification/data

### 🧹 Data Preparation and NLP

The implementation applies a structured text-processing pipeline:

**Social-media text → Text cleaning → Lowercasing → Punctuation removal → Number removal → Stopword removal → Stemming → TF-IDF**

The dataset is analysed for class distribution and text characteristics. An **80:20 stratified split** is used to maintain representative class proportions during model development and testing.

### ML Models

Four ML classifiers are evaluated:

| Model | Purpose |
|---|---|
| **Logistic Regression (LR)** | Strong linear baseline for high-dimensional TF-IDF features |
| **Multinomial Naive Bayes (MNB)** | Efficient probabilistic text-classification baseline |
| **Random Forest (RF)** | Ensemble-based classification approach |
| **XGBoost** | Gradient-boosted model capable of learning complex feature relationships |

###  Evaluation Metrics

The project uses multiple metrics rather than relying on Accuracy alone:

- **Accuracy** – overall classification correctness
- **Precision** – correctness of positive predictions
- **Recall** – ability to identify relevant positive cases
- **F1-score** – balance between Precision and Recall
- **ROC-AUC** – class-discrimination capability

The dissertation particularly emphasises the **F1-score** because it balances Precision and Recall and provides a useful measure for the multi-class classification task.

###  Hyperparameter Optimisation

HPO is applied after default model evaluation to identify stronger model configurations.

The optimisation stage demonstrates that tuning does not improve every model equally. The most important outcome is that **tuned XGBoost becomes the strongest overall model** across the evaluated measures.

###  Default Model Results

The default models establish the initial performance baseline.

| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 0.8331 | 0.8376 | 0.8331 | **0.8346** | 0.9689 |
| XGBoost | 0.8312 | 0.8504 | 0.8312 | 0.8295 | **0.9702** |
| Random Forest | 0.8227 | 0.8268 | 0.8227 | 0.8235 | 0.9615 |
| Naive Bayes | 0.7766 | 0.7661 | 0.7766 | 0.7634 | 0.9580 |

###  Default Results Interpretation

**Logistic Regression** provides the strongest default overall balance, with the highest default F1-score of **0.8346**.

**XGBoost** provides strong class-discrimination capability, achieving a default ROC-AUC of **0.9702**.

**Random Forest** provides intermediate performance.

**Naive Bayes** records the lowest F1-score of **0.7634**, suggesting that its simpler probabilistic assumptions are less suited to the complexity of the six-class task.

The default stage therefore establishes that **model selection affects the reliability of automated cyberbullying classification**.

###  Tuned Model Results

After HPO, the tuned models produce the following results:

| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 0.8331 | 0.8350 | 0.8331 | 0.8330 | 0.9695 |
| Naive Bayes | 0.7766 | 0.7661 | 0.7766 | 0.7634 | 0.9580 |
| Random Forest | 0.7932 | 0.8069 | 0.7932 | 0.7880 | 0.9570 |
| **XGBoost** | **0.8371** | **0.8493** | **0.8371** | **0.8360** | **0.9718** |

###  Best-Performing Model

The final selected model is **tuned XGBoost**.

Its final results are:

| Metric | Result |
|---|---:|
| **Accuracy** | **0.8371** |
| **Precision** | **0.8493** |
| **Recall** | **0.8371** |
| **F1-score** | **0.8360** |
| **ROC-AUC** | **0.9718** |

Tuned XGBoost provides the strongest overall balance across the evaluated measures and is therefore carried forward into SHAP analysis and the prototype.

###  SHAP Explainability

SHAP is applied to the tuned XGBoost model to explain which textual features influence classification.

The most influential features reported in the dissertation include:

1. **school**
2. **bulli**
3. **high**
4. **girl**
5. **bitch**
6. **fuck**
7. **mkr**
8. **rt**
9. **like**
10. **kid**

The feature-importance analysis identifies **“school”** as the strongest feature based on mean absolute SHAP value.

The SHAP dependence analysis also demonstrates that the contribution of **“school”** changes between observations. Some instances show negative SHAP values while others show strongly positive values. This demonstrates that the feature does not operate as a fixed classification rule; its contribution depends on the broader text representation.

###  Prototype

A functional prototype was developed to demonstrate practical six-class cyberbullying classification.

The prototype accepts user-provided social-media text and returns a predicted category.

The six supported categories are:

- **Age**
- **Ethnicity**
- **Gender**
- **Religion**
- **Other cyberbullying**
- **Not cyberbullying**

The prototype demonstrates the transition from offline ML experimentation to an interactive text-classification application.

###  Human Evaluation

The prototype includes a structured human evaluation interface with five rating factors:

| Evaluation Factor | Mean Rating |
|---|---:|
| **Ease of Use** | **4.60 / 5** |
| **Prediction Clarity** | **4.70 / 5** |
| **Prediction Relevance** | **4.80 / 5** |
| **Interface Design** | **4.70 / 5** |
| **Overall Satisfaction** | **4.70 / 5** |
| **Overall Mean** | **4.70 / 5** |

The evaluation involved **150 participant responses**.

The highest-rated factor was **Prediction Relevance (4.80/5)**. Prediction Clarity, Interface Design and Overall Satisfaction each achieved **4.70/5**. Ease of Use achieved **4.60/5**.

The overall mean of **4.70/5** indicates a consistently positive evaluation of the prototype across usability, clarity, relevance, interface design and satisfaction.

###  System Testing

Testing covers the workflow from text input through final classification.

| Testing Area | Method | Purpose |
|---|---|---|
| Preprocessing | Manual testing | Verify text cleaning and TF-IDF |
| ML Prediction | Test cases | Verify six-class outputs |
| Model Performance | Accuracy, Precision, Recall, F1-score, ROC-AUC | Assess classifier effectiveness |
| Prototype | Functional testing | Verify input and prediction |
| Human Evaluation | User feedback | Assess usability and experience |

### Ethics and Data Governance

The project addresses:

- Privacy
- Bias
- Participant safety
- Data security

The research uses a **secondary dataset** and does not involve direct collection of identifiable personal information. The dissertation also reports **UREC2 approval** and informed consent procedures for human evaluation.

###  Research Contribution

The project contributes an integrated workflow combining:

**NLP → TF-IDF → ML models → Multi-metric evaluation → HPO → Best model selection → SHAP → Prototype → Human evaluation**

The main contribution is not only the final classifier, but the integration of **performance evaluation, optimisation, interpretability and practical user assessment** within a single six-class cyberbullying classification workflow.

### Strengths

- Six-class rather than simple binary classification
- Evaluation of four ML approaches
- Multiple performance metrics
- HPO for model configuration
- SHAP-based feature interpretation
- Functional prototype
- Structured human evaluation
- Integrated technical and practical assessment

### Limitations

The dissertation identifies several limitations:

1. The study relies on a **single dataset**, which may restrict generalisation to other platforms and populations.
2. Text-based analysis provides limited contextual information for repeated or conversational cyberbullying behaviour.
3. Human evaluation reflects the selected participant group and may not represent every potential user population.

### Future Work

The dissertation recommends extending the project through more advanced techniques:

**Fine-tuned Sentence-BERT** could provide richer contextual representations than TF-IDF.

**Multimodal classification** could combine text and image information for broader social-media analysis.

**Privacy-preserving federated learning** could support distributed deployment while reducing the need for centralised user data.

**Transformer-based multilingual models** could improve classification in linguistic environments where conventional NLP resources are limited.



###  Final Outcome

The final system identifies **tuned XGBoost** as the best-performing model, achieving an **F1-score of 0.8360** and **ROC-AUC of 0.9718**. SHAP adds model interpretability, the prototype demonstrates six-class practical classification, and human evaluation records an overall mean of **4.70/5**.

