# PII-data-detection in student writing
Model was developed using DeBERTa v3 transformer model for detecting personally identifiable information (PII) in student writing for a kaggle competition. Several other transformer models were initially considered but DeBERTa v3 outperformed other models on 'recall' with a score of 98%, which was the evaluation metric for the project (RoBERTa 88%, SpaCy large 84%, PIILO 87%). 

During data pre-processing, several approaches were taken. Splitting the student texts further by limiting the number of input tokens to 400 (to make sure it does not exceed the pre-trained context length of 512), and increasing the training data set by using augmented data sets. Former method proved to be successful since it increased the 'recall' by 4%, but later approach did not make an impact. 

The competition details can be found below,

# Overview
The goal of this competition is to develop a model that detects personally identifiable information (PII) in student writing. Your efforts to automate the detection and removal of PII from educational data will lower the cost of releasing educational datasets. This will support learning science research and the development of educational tools.

Reliable automated techniques could allow researchers and industry to tap into the potential that large public educational datasets offer to support the development of effective tools and interventions for supporting teachers and students.

# Description
In today’s era of abundant educational data from sources such as ed tech, online learning, and research, widespread PII is a key challenge. PII’s presence is a barrier to analyze and create open datasets that advance education because releasing the data publicly puts students at risk. To reduce these risks, it’s crucial to screen and cleanse educational data for PII before public release, which data science could streamline.
Manually reviewing the entire dataset for PII is currently the most reliable screening method, but this results in significant costs and restricts the scalability of educational datasets. While techniques for automatic PII detection that rely on named entity recognition (NER) exist, these work best for PII that share common formatting such as emails and phone numbers. PII detection systems struggle to correctly label names and distinguish between names that are sensitive (e.g., a student's name) and those that are not (e.g., a cited author).
Competition host Vanderbilt University is a private research university in Nashville, Tennessee. It offers 70 undergraduate majors and a full range of graduate and professional degrees across 10 schools and colleges, all on a beautiful campus with state-of-the-art laboratories. Vanderbilt is optimized to inspire and nurture cross-disciplinary research that fosters groundbreaking discoveries.
For this competition, Vanderbilt has partnered with The Learning Agency Lab, an Arizona-based independent nonprofit focused on developing the science of learning-based tools and programs for the social good.
Your work in creating reliable automated techniques to detect PII will lead to more high-quality public educational datasets. Researchers can then tap into the potential of this previously unavailable data to develop effective tools and interventions that benefit both teachers and students.

# Evaluation
Submissions are evaluated on micro Fβ, which is a classification metric that assigns value to recall and precision. The value of β is set to 5, which means that recall is weighted 5 times more heavily than precision.

# Submission File
For each document in the test set, you must predict which token values have a positive PII label. You should only include predictions of positive PII label values. Outside labels O should not be included. Each row in the submission should correspond to a single label found at a unique document-token pair. Additionally, the evaluation metric requires a row_id with an enumeration of predicted labels.

The file should contain a header and have the following format:

row_id,document,token,label
0,7,9,B-NAME_STUDENT <br />
1,7,10,I-NAME_STUDENT <br />
2,10,0,B-NAME_STUDENT
etc.

Competition link - https://www.kaggle.com/competitions/pii-detection-removal-from-educational-data
