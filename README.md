# PII Data Detection in Student Writing

This project was developed for a Kaggle competition focused on detecting Personally Identifiable Information (PII) in student writing. The primary objective was to build a robust model capable of identifying PII with high recall. The DeBERTa v3 transformer model was chosen for this task after comparing its performance with other transformer models.

## Table of Contents
1. [Introduction](#introduction)
2. [Data Loading & Preprocessing](#data-loading-and-preprocessing)
3. [Data Augmentation](#data-augmentation)
4. [Feature Engineering](#feature-engineering)
5. [Model Building & Training](#model-building-and-training)
6. [Inference](#inference)
7. [Results](#results)
8. [Conclusion](#conclusion)
9. [Acknowledgments](#acknowledgments)

## Introduction
The detection of Personally Identifiable Information (PII) is crucial in maintaining privacy and data security. This project utilizes state-of-the-art transformer models to identify PII in student writing. DeBERTa v3 was selected for its superior performance in recall, achieving a score of 98%.

## Data Loading and Preprocessing
Data loading and preprocessing are critical steps in any machine learning project. The following steps were undertaken:

1. **Loading Data**: The dataset was loaded into the environment using pandas.
2. **Splitting Texts**: Student texts were split to ensure each segment did not exceed 400 tokens. This was done to fit within the pre-trained context length of 512 tokens of the DeBERTa model.
3. **Tokenization**: The texts were tokenized using the DeBERTa tokenizer.
4. **Label Encoding**: Labels for PII were encoded to match the input tokens.

The preprocessing steps improved recall by 4%.

## Data Augmentation
Several data augmentation techniques were explored to increase the size of the training dataset:

1. **Synonym Replacement**: Replacing words with their synonyms.
2. **Random Insertion**: Inserting random words at random positions in the text.
3. **Random Swap**: Swapping the positions of two words in the text.
4. **Random Deletion**: Deleting random words from the text.

However, these methods did not significantly impact the recall score.

## Feature Engineering
Feature engineering was minimal due to the nature of transformer models, which excel at capturing contextual information from raw text. The primary features included:

1. **Tokenized Texts**: The raw texts converted into tokens.
2. **Attention Masks**: Masks to indicate which tokens should be attended to by the model.

## Model Building and Training
The DeBERTa v3 model was selected after comparing several transformer models:

1. **Model Comparison**:
   - RoBERTa: Recall 88%
   - SpaCy Large: Recall 84%
   - PIILO: Recall 87%
   - DeBERTa v3: Recall 98%

2. **Training Setup**:
   - **Optimizer**: AdamW
   - **Learning Rate**: Adjusted using a learning rate scheduler.
   - **Loss Function**: Cross-Entropy Loss
   - **Early Stopping**: Implemented to prevent overfitting.
   - **Batch Size**: Set according to available GPU memory.

3. **Training Process**:
   - The model was trained on the preprocessed data.
   - Early stopping was used to monitor validation loss and stop training when no improvement was observed.

## Inference
The trained model was used to predict PII on unseen data:

1. **Text Splitting**: Similar to preprocessing, texts were split into manageable segments.
2. **Tokenization**: The segments were tokenized.
3. **Prediction**: The model predicted the presence of PII in each segment.
4. **Aggregation**: Results from all segments were combined to produce the final output.

## Results
The DeBERTa v3 model achieved a recall score of 98%, significantly outperforming other models considered for this task. This high recall is crucial for PII detection, ensuring that most instances of PII are correctly identified.

## Conclusion
The DeBERTa v3 transformer model proved to be highly effective in detecting PII in student writing, achieving an outstanding recall score. The project demonstrates the importance of careful preprocessing and model selection in achieving optimal results.

**Competition link** - https://www.kaggle.com/competitions/pii-detection-removal-from-educational-data
