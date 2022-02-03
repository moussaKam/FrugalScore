# FrugalScore
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

You can run the example by using the following command:

```
python run_frugalscore.py \
  --model_name_or_path moussaKam/frugalscore_tiny_bert-base_bert-score \
  --train_file examplefile.json --validation_file examplefile.json \
  --test_file examplefile.json \
  --output_dir predictions \
  --max_seq_length 512 \
  --per_device_eval_batch_size 32 \
  --overwrite_output_dir \
  --do_predict
```

Make sure you download the `datasets` package and the`transformars` package from source. 
```
pip install git+https://github.com/huggingface/datasets
pip install git+https://github.com/huggingface/transformers
```
