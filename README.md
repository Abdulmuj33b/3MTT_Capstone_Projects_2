# 3MTT_Capstone_Projects_2

Summary:
Data Analysis Key Findings
The project aims to build a Fake News Detection System using a Random Forest Classifier, involving phases of data loading and cleaning, text preprocessing, feature engineering, model training, evaluation, and insights derivation.
A robust data loading function handles potential file and encoding issues from fake.csv.
Missing values are assessed, critical columns are identified, and column names are standardized, with placeholders created if critical columns are absent.
Text cleaning involves a multi-step pipeline: handling non-string values, removing HTML tags, URLs, and special characters, normalizing whitespace, and removing empty texts.
Text normalization converts text to lowercase and removes numbers and most special punctuation.
Lemmatization reduces words to their base form, preferentially using spaCy and falling back to NLTK.
Publication dates are processed to handle various formats, normalize timezones to UTC, and fill missing dates.
Feature engineering includes extracting linguistic features (word count, character count, average word length), calculating sentiment polarity using TextBlob, extracting domain names from URLs, and applying TF-IDF vectorization with specified parameters (max_features=1000, ngram_range=(1, 2), stop_words='english', min_df=5, max_df=0.7).
All features (linguistic, sentiment, temporal, domain, TF-IDF) are combined into a single feature matrix, with remaining missing values filled with 0.
The target variable is created based on keywords in the 'type' column, labeling news as fake (1) or real (0), with a synthetic target created if no fake samples are detected.
Data is split into 80% training and 20% testing sets using stratified sampling to maintain class proportions.
Class imbalance is handled using SMOTE on the training data if the minority class has at least 5 samples; otherwise, class weights are used in the model.
A Random Forest Classifier is trained with specific parameters (n_estimators=200, max_depth=15, min_samples_leaf=2, class_weight='balanced_subsample' or None).
Model evaluation is performed on the test set, generating predictions and probabilities for metrics like Precision, Recall, F1-score, and ROC-AUC.
A confusion matrix and ROC curve are generated to visualize performance.
The top 20 most important features from the trained Random Forest model are identified and visualized.
The trained model is saved using joblib.
Key insights from data analysis include observations on linguistic characteristics (fake news having higher word/character counts and more extreme sentiment), temporal publication patterns, and domain analysis.
Ethical considerations include subjectivity in labeling, transparency with confidence scores, algorithmic bias, and the need for regular audits.
Recommendations for future improvements cover system enhancements (model ensembles, external credibility scores, social media metrics, browser extension), public education (media literacy modules, awareness campaigns, library partnerships), and policy advocacy (transparency, anti-disinformation legislation, international standards).
The project aims to combat misinformation by automatically identifying potentially fake content and contributing to a more informed public sphere.
Insights or Next Steps
The project provides a solid framework for fake news detection, highlighting the importance of robust data handling and diverse feature engineering. Future work should prioritize implementing the recommended system improvements, such as model ensembles and integrating external credibility scores, to potentially enhance detection accuracy further.
Recognizing the ethical challenges, particularly algorithmic bias and labeling subjectivity, is crucial. Subsequent development cycles should include dedicated efforts for bias detection and mitigation, along with user-facing components that communicate classification confidence and the inherent limitations of the system.
