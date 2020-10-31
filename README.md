# gender-bias-in-IR
This repository contains the code and resources for detecting the gender of queries (Female, Male, Neutral). Baed on a fine-tuned BERT model, we show how queries can be labelled for gender at scale. In order to fine-tune BERT, we used some of the MS MARCO dev set queries that have been labelled by Navid Rekabsaz (the queries can be found [here](https://github.com/navid-rekabsaz/GenderBias_IR/blob/master/resources/queries_gender_annotated.csv)). Subsequently, we used the fine-tuned BERT model to classify the gender of other MS MARCO dev set queries at scale.
## Code:
- codes/train.py: The code for fine-tuning BERT on the [gender-annotated dataset](https://github.com/navid-rekabsaz/GenderBias_IR/blob/master/resources/queries_gender_annotated.csv).
- codes/predict.py: You can use this code to identify the gender of the queries by the fine-tuned model.
## Trained Model:
You can also use the fine-tuned BERT model for query gender identification [here](https://drive.google.com/file/d/1_YTRs4v5DVUGUffnRHS_3Yk4qteJKO6w/view?usp=sharing).
## Results:
We have 
