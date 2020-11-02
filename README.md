# Exploring Gender Biases in Information Retrieval Relevance Judgement Datasets
This repository contains the code and resources for detecting the gender of queries (Female, Male, Neutral) along with psychological characteristics of their relevance judgement documents. 
## Query Gender Identification:
As the first step and in order to be able to label queries based on their gender at scale, we employed the dataset released by Navid Rekabsaz to train relevant classifiers. This [dataset](https://github.com/navid-rekabsaz/GenderBias_IR/blob/master/resources/queries_gender_annotated.csv) consists of 742 female, 1,202 male and 1,765 neutral queries. We removed the 41 queries related to the "Other or Multiple Genders" class as there were not sufficient instances to train a classifier. Substequently, we trained various types of  classifiers on this dataset and in order to evaluate the performance of the classifiers, we adopt a 5-fold cross-validation strategy.
|          Category         |        Classifier       |  Accuracy | Female F1-Score | Male F1-Score | Neutral F1-Score |
|:-------------------------:|:-----------------------:|:---------:|:--------:|:--------:|:-------:|
|      Dynamic Embeddings   |    BERT_base_uncased    |   0.856   |   0.816  |   0.872  |  0.862  |
|                           | DistilBERT_base_uncased |   0.847   |   0.815  |   0.861  |  0.853  |
|                           |         RoBERTa         |   0.810   |   0.733  |   0.820  |  0.836  |
|                           |  DistilBERT_base_cased  |   0.800   |   0.730  |   0.823  |  0.833  |
|                           |     BERT_base_cased     |   0.797   |   0.710  |   0.805  |  0.827  |
|                           |     XLNet_base_cased    |   0.795   |   0.710  |   0.805  |  0.826  |
|      Static Embeddings    |         Word2Vec        |   0.757   |   0.626  |   0.756  |  0.809  |
|                           |         fastText        |   0.750   |   0.615  |   0.759  |  0.792  |

In the table above the performance of each of the developed classifiers is reported. As shown the uncased fine-tuned BERT model shows the best
performance for query gender identification.


- codes/train.py: The code for fine-tuning BERT model on the [gender-annotated dataset](https://github.com/navid-rekabsaz/GenderBias_IR/blob/master/resources/queries_gender_annotated.csv).
- codes/predict.py: You can use this code to identify the gender of the queries by the fine-tuned model.
## Trained Model:
You can also use the fine-tuned BERT model for your query gender identification task [here](https://drive.google.com/file/d/1_YTRs4v5DVUGUffnRHS_3Yk4qteJKO6w/view?usp=sharing).
## Results:
Psychological characteristics related to the queries of each group can be found in Quantifying Psychological Characteristics folder.
