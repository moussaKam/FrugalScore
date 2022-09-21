# FrugalScore

<p>
<a href="https://console.tiyaro.ai/explore/huggingface-moussaKam-frugalscore_tiny_bert-base_bert-score-1"> <img src="https://tiyaro-public-docs.s3.us-west-2.amazonaws.com/assets/try_on_tiyaro_badge.svg"></a>
</p>
FrugalScore is an approach to learn a fixed, low cost version of any expensive NLG metric, while retaining most of its original performance

Paper: https://arxiv.org/abs/2110.08559?context=cs

The pretrained checkpoints presented in the paper can be found on the [huggingface models hub](https://huggingface.co/moussaKam)

| FrugalScore                                        | Student     | Teacher        | Method     |
|----------------------------------------------------|-------------|----------------|------------|
| moussaKam/frugalscore_tiny_bert-base_bert-score    | BERT-tiny   | BERT-Base      | BERTScore  |
| moussaKam/frugalscore_small_bert-base_bert-score   | BERT-small  | BERT-Base      | BERTScore  |
| moussaKam/frugalscore_medium_bert-base_bert-score  | BERT-medium | BERT-Base      | BERTScore  |
| moussaKam/frugalscore_tiny_roberta_bert-score      | BERT-tiny   | RoBERTa-Large  | BERTScore  |
| moussaKam/frugalscore_small_roberta_bert-score     | BERT-small  | RoBERTa-Large  | BERTScore  |
| moussaKam/frugalscore_medium_roberta_bert-score    | BERT-medium | RoBERTa-Large  | BERTScore  |
| moussaKam/frugalscore_tiny_deberta_bert-score      | BERT-tiny   | DeBERTa-XLarge | BERTScore  |
| moussaKam/frugalscore_small_deberta_bert-score     | BERT-small  | DeBERTa-XLarge | BERTScore  |
| moussaKam/frugalscore_medium_deberta_bert-score    | BERT-medium | DeBERTa-XLarge | BERTScore  |
| moussaKam/frugalscore_tiny_bert-base_mover-score   | BERT-tiny   | BERT-Base      | MoverScore |
| moussaKam/frugalscore_small_bert-base_mover-score  | BERT-small  | BERT-Base      | MoverScore |
| moussaKam/frugalscore_medium_bert-base_mover-score | BERT-medium | BERT-Base      | MoverScore |

# Experiments on [BEAMetrics](https://github.com/ThomasScialom/BEAMetrics) benchmark
We evaluate our three models `frugalscore_(tiny/small/medium)_bert-base_bert-score` different datasets includeded in `BEAMetrics` benchmark. The results are comparable to the second block of Table 2 reported in the [paper](https://arxiv.org/pdf/2110.09147.pdf).

|               | WMT  | Web  | Asv  | MUS  | Fli  | ReaSum | SumE | OpQA | OkVQA |
| ------------- | :--: | :--: | :--: | :--: | :--: | :----: | :--: | :--: | :---: |
| BERTScore_f1  | 20.5 | 60.8 | 61.4 | 37.5 | 33.5 | 39.3   | 12.4 | 12.4 | 6.2   |
| Frugal_tiny   | 16.6 | 71.5 | 44.0 | 52.3 | 49.8 | 46.4   | 18.7 | 29.2 | 20.1  |
| Frugal_small  | 18.4 | 72.1 | 52.9 | 48.2 | 54.1 | 48.9   | 15.2 | 28.2 | 14.3  |
| Frugal_medium | 19.7 | 73.4 | 58.4 | 45.9 | 54.2 | 49.4   | 16.4 | 24.7 | 16.1  |

Note that `bert-base-multilingual-cased` is used to generate BERTScore. 

To use the metric:

```python
from datasets import load_metric
metric = load_metric('frugalscore.py')

references = ['hello world', 'this is an example']
predictions = ['hello there', 'this is a good example']

scores = metric.compute(references=references, predictions=predictions)

print(scores)
```
`{'scores': [0.631, 0.864]}`

Make sure you have the latest verions of the `datasets` and `transformers` installed:
```
pip install --upgrade datasets
pip install --upgrade transformers
```
