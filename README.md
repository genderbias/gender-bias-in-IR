# gender-bias-in-IR
This repository contains the code and resources for measuring stereotypical biases in gold standard documents of MSMarco.
## Code:
- codes/train.py: The code for fine-tuning BERT on the [gender-annotated dataset](https://github.com/navid-rekabsaz/GenderBias_IR/blob/master/resources/queries_gender_annotated.csv).
- codes/predict.py: You can also use this code to identify the gender of the queries by the fine-tuned model.
## Trained Model:
You can also use the fine-tuned BERT model for query gender identification [here](https://drive.google.com/file/d/1_YTRs4v5DVUGUffnRHS_3Yk4qteJKO6w/view?usp=sharing).
## Results:
The results of LIWC toolkit on the MS MARCO relevance judgements documents on each gender group (Female, Male, Neutral) can be found in the LIWCS_Reults folder.
