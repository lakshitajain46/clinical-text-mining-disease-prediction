# Clinical Text Mining for Disease Prediction

A Natural Language Processing (NLP) and machine-learning project exploring the classification of clinical transcriptions into medical specialties using TF-IDF feature extraction and Logistic Regression.

## Project Overview

Clinical documents contain valuable information about symptoms, diagnoses, medical history, and treatment. This project explores how NLP and supervised machine learning can process unstructured medical transcription text and automatically classify it by medical specialty.

**Note:** The current implementation predicts medical specialties, not individual disease diagnoses.

## Dataset

- **Dataset:** Medical Transcriptions (MTSamples)
- **Source:** [Kaggle — Medical Transcriptions](https://www.kaggle.com/datasets/tboyle10/medicaltranscriptions)
- **Input:** Clinical transcription text
- **Target:** Medical specialty

The notebook identifies the transcription and specialty columns and standardizes them for processing.

## Methodology

1. **Data loading:** Load the CSV dataset using Pandas.
2. **Text preprocessing:** Convert text to lowercase, tokenize, lemmatize, and remove stop words and non-alphabetic tokens using spaCy.
3. **Feature extraction:** Convert cleaned text into TF-IDF features using `max_features=5000` and `ngram_range=(1,2)`.
4. **Data splitting:** Use a stratified 70:30 training-test split.
5. **Model training:** Train a Logistic Regression classifier with `max_iter=500`.
6. **Evaluation:** Generate a classification report and confusion matrix.
7. **Prediction and saving:** Demonstrate a prediction on sample text and save the trained model and vectorizer using Joblib.

## Technologies Used

- Python
- Pandas and NumPy
- spaCy
- Scikit-learn
- TF-IDF
- Logistic Regression
- Matplotlib and Seaborn
- Joblib
- Google Colab

## Results

The saved notebook output reports the following results on a test set of 1,500 examples:

| Metric | Recorded result |
|---|---:|
| Test examples | 1,500 |
| Test accuracy | 28% |
| Macro F1-score | 0.09 |
| Weighted F1-score | 0.23 |

These results indicate limited classification performance across medical specialties. Some classes have zero precision or recall, highlighting the difficulty of predicting underrepresented or challenging categories.

**Evaluation note:** The current notebook fits the TF-IDF vectorizer before splitting the data into training and test sets. This can introduce data leakage and affect the reported metrics. The results should therefore be treated as preliminary rather than as an independent estimate of model generalization.

## Visualizations

Selected medical specialty analysis graphs are available in the accompanying PDF:

[**View Medical Specialty Analysis Graphs (PDF)**](medical_specialty_analysis_graphs.pdf)

The notebook also generates a classification report and confusion matrix to examine model performance across medical specialties.

## Limitations

- The dataset contains imbalanced medical-specialty categories.
- The current model has limited classification performance across many classes.
- TF-IDF and Logistic Regression may not capture the full context of clinical language.
- The current evaluation workflow may introduce data leakage through TF-IDF feature fitting before the train-test split.
- A stratified random split does not establish generalization to independent hospitals or datasets.
- This is an academic project, not a clinically validated diagnostic system.

## Future Work

- Fit the TF-IDF vectorizer on training data only, using a leakage-free evaluation pipeline.
- Address class imbalance using suitable training-only resampling or class weighting.
- Compare alternative models and tune hyperparameters.
- Evaluate macro F1-score, per-class recall, and confusion patterns.
- Compare TF-IDF with biomedical language models such as BioBERT or ClinicalBERT.
- Evaluate on independent clinical datasets when suitable data are available.

## Repository Contents

- `Clinical_Text_Mining_Disease_Prediction.ipynb` — notebook containing the implementation and recorded outputs.
- `README.md` — project documentation.
- `medical_specialty_analysis_graphs.pdf` — selected medical specialty analysis visualizations.

## Disclaimer

This project is intended for educational and research purposes only. Its outputs must not be used for medical diagnosis or clinical decision-making.

## Author

**Lakshita Jain**  
B.Tech. Biomedical Engineering  
Shri G. S. Institute of Technology and Science (SGSITS), Indore

- GitHub: [lakshitajain46](https://github.com/lakshitajain46)
- LinkedIn: [Lakshita Jain](https://www.linkedin.com/in/lakshita-jain-143076368/)
