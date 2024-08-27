
# SSN-NLP @ CheckThat! Subjectivity Detection

This repository contains the data and python files for Task 2 of the CheckThat! Lab for CLEF 2024, for Subjectivity Detection. 

Task 2 of the CheckThat! Lab at CLEF 2024 requires the development of systems to distinguish whether a sentence from a news article expresses the subjective view of the author behind it or presents an objective view on the covered topic instead. This is a binary classification tasks in which systems have to identify whether a text sequence (a sentence or a paragraph) is subjective or objective.
Systems for subjectivity detection in the context of political bias must aim to accurately discern the underlying tone and intention of textual content. They should be designed to recognize linguistic cues, sentiment indicators, and contextual nuances that signify subjective viewpoints or objectivity in news reporting. Effective subjectivity detection systems should also be able to differentiate between facts, opinions, and emotional expressions, considering the potential influence of language patterns and rhetorical strategies used in political discourse.


Our team SSN-NLP ranked third out of 16 submission (including the baseline evaluation), with a macro-average F1 score of 0.71. 

## Paper
The paper describing the proposed method can be found here:

[From Feature-based Algorithms to Transformers: A Study on Detecting Subjectivity](https://ceur-ws.org/Vol-3740/paper-52.pdf)



## Models

Three types of methods are used:

    1. Machine Learning Models with POS Tag Extraction
    2. RNNs and GRUs
    3. Transformer-based Models
## Machine Learning Models

Based on the work by Rizk and Awad (2018), additional features to help classify subjectivity and objectivity are added using POS Tags. Quotations, past tense verbs, third person pronoungs, numerical values and dates correspond to objectivity, whereas POS tags like imperative verbs, exclamation and question marks, first and second person verbs correspond to subjectivity.

These features are added to the existing dataset with sentences and labels. 

The results obtained on the development test set are as follows:

| Model                        | Accuracy | Macro-Averaged-F1-Score |
|------------------------------|----------|-------------------------|
| Logistic Regression with POS | 0.56     | 0.53                    |
| Random Forest with POS       | 0.53     | 0.45                    |
| Gradient Boosting wth POS    | 0.55     | 0.5                     |
| KNN with POS                 | 0.6      | 0.6                     |
| SVM with POS                 | 0.56     | 0.54                    |








## RNNs and GRUs

following LSTM, BiLSTM and GRU systems were trained to detect subjectivity. A grid search method was used to identify the best activation function, loss function and optimizer.

The following table shows the results of these models on the development test set:

|     Model                    |     Accuracy    |     Macro-Averaged-F1-Score    |
|------------------------------|-----------------|--------------------------------|
|     BiLSTM                   |     0.47        |     0.32                       |
|     BiLSTM with Attention    |     0.5         |     0.34                       |
|     GRU                      |     0.47        |     0.32                       |




## Transformer Models

Multiple transformer models including BERT, mBERT, RoBERTa, XLMRoBERTa, deBERTa, deBERTa V3, DistilBERT were fine-tuned to detect subjectivity. 

The training parameters used are as follows:

| Parameter            | Configuration                 |
|----------------------|-------------------------------|
|     GPU and RAM      |     A100 GPU and 80 GB RAM    |
|     Epochs           |     3                         |
|     Learning Rate    |     2e-5                      |
|     Batch Size       |     16                        |
|     Optimizer        |     AdamW                     |
|     Loss Function    |     Cross-Entropy Loss        |



The results on the development test set are as follows:

|     Model                                          |     Accuracy    |     Macro-Averaged-F1-Score    |
|----------------------------------------------------|-----------------|--------------------------------|
|     DistilBERT                                     |     0.71        |     0.7                        |
|     BERT-base-uncased                              |     0.74        |     0.74                       |
|     BERT-large-uncased                             |     0.703       |     0.702                      |
|     mBERT                                          |     0.707       |     0.701                      |
|     RoBERTa                                        |     0.806       |     0.804                      |
|     XLMRoBERTa                                     |     0.71        |     0.71                       |
|     deBERTa                                        |     0.72        |     0.71                       |
|     mdeBERTa   V3                                  |     0.79        |     0.79                       |
|     XLNet                                          |     0.78        |     0.78                       |
|     RoBERTa   with additional POS Tags features    |     0.8189      |     0.8185                     |


The RoBERTa model with additional POS tag features performed the best. 
## Authors


- [Pooja Premnath](https://github.com/PoojaPremnath2003)
- [VS Pranav](https://github.com/vspr14)



## References

1.	Rizk, Yara, and Mariette Awad. "Syntactic genetic algorithm for a subjectivity analysis of sports articles.
2.	Barrón-Cedeño, Alberto, et al. "The CLEF-2024 CheckThat! Lab: Check-Worthiness, Subjectivity, Persuasion, Roles, Authorities, and Adversarial Robustness." European Conference on Information Retrieval. Cham: Springer Nature Switzerland, 2024.

## Citation

If you find our work helpful, please consider including the following citation:


```
@inproceedings{DBLP:conf/clef/PremnathSSB24,
  author       = {Pooja Premnath and
                  Pranav Vaithiya Subramani and
                  Nilu R. Salim and
                  Bharathi B},
  title        = {{SSN-NLP} at CheckThat! 2024: From Feature-based Algorithms to Transformers:
                  {A} Study on Detecting Subjectivity},
  booktitle    = {{CLEF} (Working Notes)},
  series       = {{CEUR} Workshop Proceedings},
  volume       = {3740},
  pages        = {570--579},
  publisher    = {CEUR-WS.org},
  year         = {2024}
}

```
