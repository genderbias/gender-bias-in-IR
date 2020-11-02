# Exploring Gender Biases in Information Retrieval Relevance Judgement Datasets
This repository contains the code and resources for detecting the gender of queries (Female, Male, Neutral) along with psychological characteristics of their relevance judgement documents. 
## Query Gender Identification:
As the first step and in order to be able to label gendered queries at scale, we employed the dataset released by Navid Rekabsaz. The [dataset](https://github.com/navid-rekabsaz/GenderBias_IR/blob/master/resources/queries_gender_annotated.csv) consists of 742 female, 1,202 male and 1,765 neutral queries. We removed the 41 queries related to the "Other or Multiple Genders" class as there were not sufficient instances to train a classifier.


- codes/train.py: The code for fine-tuning BERT model on the [gender-annotated dataset](https://github.com/navid-rekabsaz/GenderBias_IR/blob/master/resources/queries_gender_annotated.csv).
- codes/predict.py: You can use this code to identify the gender of the queries by the fine-tuned model.
## Trained Model:
You can also use the fine-tuned BERT model for your query gender identification task [here](https://drive.google.com/file/d/1_YTRs4v5DVUGUffnRHS_3Yk4qteJKO6w/view?usp=sharing).
## Results:
Psychological characteristics related to the queries of each group can be found in Quantifying Psychological Characteristics folder.
