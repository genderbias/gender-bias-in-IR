# Exploring Gender Biases in Information Retrieval Relevance Judgement Datasets
This repository contains the code and resources for detecting the gender of queries (Female, Male, Neutral) along with psychological characteristics of their relevance judgement documents. 
## Query Gender Identification and Labeling
In this work, we proposed a Query Gender classifier. As the first step and in order to be able to label queries based on their gender at scale, we employed the [gender-annotated dataset](https://github.com/navid-rekabsaz/GenderBias_IR/blob/master/resources/queries_gender_annotated.csv) released by Navid Rekabsaz to train relevant classifiers. This dataset consists of 742 female, 1,202 male and 1,765 neutral queries. We trained various types of  classifiers on this dataset and in order to evaluate the performance of the classifiers, we adopt a 5-fold cross-validation strategy.
|          Category         |        Classifier       |  Accuracy | Female   F1-Score | Male   F1-Score | Neutral   F1-Score |
|:-------------------------:|:-----------------------:|:---------:|:--------:|:--------:|:-------:|
|      Dynamic Embeddings   |    BERT_base_uncased    |   0.856   |   0.816  |   0.872  |  0.862  |
|                           | DistilBERT_base_uncased |   0.847   |   0.815  |   0.861  |  0.853  |
|                           |         RoBERTa         |   0.810   |   0.733  |   0.820  |  0.836  |
|                           |  DistilBERT_base_cased  |   0.800   |   0.730  |   0.823  |  0.833  |
|                           |     BERT_base_cased     |   0.797   |   0.710  |   0.805  |  0.827  |
|                           |     XLNet_base_cased    |   0.795   |   0.710  |   0.805  |  0.826  |
|      Static Embeddings    |         Word2Vec        |   0.757   |   0.626  |   0.756  |  0.809  |
|                           |         fastText        |   0.750   |   0.615  |   0.759  |  0.792  |
<table>
<tbody>
<tr>
  <td  rowspan="2">Category</td>
  <td  rowspan="2">Classifier</td>
  <td  rowspan="2">Accuracy</td>

</tr>

<tr>
  <td>Female</td>
  <td>Male</td>
  <td>Neutral</td>
</tr>

<tr>
<td  rowspan="6">Dynamic Embeddings</td>
  <td>BERT_base_uncased</td>
  <td>0.856</td>
  <td>0.816</td>
  <td>0.872</td>
  <td>0.862</td>
</tr>
<tr>
  <td>DistilBERT_base_uncased</td>
  <td>0.847</td>
  <td>0.815</td>
  <td>0.872</td>
  <td>0.862</td>
</tr>
<tr>
  <td>BERT_base_uncased</td>
  <td>0.856</td>
  <td>0.816</td>
  <td>0.861</td>
  <td>0.853</td>
</tr>

<tr>
  <td>BERT_base_uncased</td>
  <td>0.856</td>
  <td>0.816</td>
  <td>0.872</td>
  <td>0.862</td>
</tr>
</tbody>
</table>

In the table above the performance of each of the developed classifiers is reported. As shown the uncased **fine-tuned BERT** model shows the best
performance for query gender identification. Finally, for the purpose of measuring bias in relevance judgements, we used our best-performed model to identify the gender of queries in MS MARCO Dev set that had at least one related human-judged relevance judgement document - equivalent to 51,827 queries. Note that, the queries of gender-annotated dataset were removed from this dataset to avoid unintended leakage.

The following table illustrates a few queries labeled using our fine-tuned BERT classifier.
| QID     | Query                                        | Predicted Gender |
|---------|----------------------------------------------|------------------|
| 80095   | Can you take naproxen during **pregnancy**       | Female           |
| 14757   | **aimee osbourne** net worth                     | Female           |
| 1055525 | what is **estrogen** dominance in **women**          | Female           |
| 189154  | foods that can prevent **prostate** cancer       | Male             |
| 11251   | **adam devine** net worth                        | Male             |
| 227637  | what depletes **testosterone** in **men**            | Male             |
| 40234   | average percentage of accepted scholarships  | Neutral          |
| 22992   | are humans still considered animals          | Neutral          |
| 362845  | how to get students loans without a cosigner | Neutral          |

### Code
- `code/train.py`: The code for fine-tuning BERT on queries_gender_annotated dataset or any other dataset.
- `codes/predict.py`: In any case that you do not want to train the model, you can download the pre-trianed model and use predict.py  for predicting the gender of queries.
### Fine_Tuned Model
You can also use the [fine-tuned BERT model](https://drive.google.com/file/d/1_YTRs4v5DVUGUffnRHS_3Yk4qteJKO6w/view?usp=sharing), which has been already trained on queries_gender_annotated dataset, as your pre-trained model and use it for your query gender identification task. You can load the model and fine-tune it using `code/train.py` and also predict the gender of queries by running `codes/predict.py`.
## Psychological Characteristics Quantification
Our approach for quantifying bias is based on measuring different psychological characteristics of the relevance judgement documents associated with each query. To investigate this, we employ Linguistic Inquiry and Word Count (LIWC) text analytics toolkit to compute the degree to which different psychological characteristics are observed in relevance judgement documents. These Psychological characteristics related to the queries of each group can be found in `results/psychological analysis` folder.

