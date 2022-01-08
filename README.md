# FrugalScore
FrugalScore is an approach to learn a fixed, low cost version of any expensive NLG metric, while retaining most of its original performance

Paper: https://arxiv.org/abs/2110.08559?context=cs

The pretrained checkpoints presented in the paper can be found on the [huggingface models hub](https://huggingface.co/moussaKam)

| FrugalScore                                        | Student     | Teacher        | Method     |
|----------------------------------------------------|-------------|----------------|------------|
| moussaKam/frugalscore_tiny_bert-base_bert-score    | BERT-tiny   | BERT-base      | BERTScore  |
| moussaKam/frugalscore_small_bert-base_bert-score   | BERT-small  | BERT-base      | BERTScore  |
| moussaKam/frugalscore_medium_bert-base_bert-score  | BERT-medium | BERT-base      | BERTScore  |
| moussaKam/frugalscore_tiny_roberta_bert-score      | BERT-tiny   | RoBERTa        | BERTScore  |
| moussaKam/frugalscore_small_roberta_bert-score     | BERT-small  | RoBERTa        | BERTScore  |
| moussaKam/frugalscore_medium_roberta_bert-score    | BERT-medium | RoBERTa        | BERTScore  |
| moussaKam/frugalscore_tiny_deberta_bert-score      | BERT-tiny   | DeBERTa-XLarge | BERTScore  |
| moussaKam/frugalscore_small_deberta_bert-score     | BERT-small  | DeBERTa-XLarge | BERTScore  |
| moussaKam/frugalscore_medium_deberta_bert-score    | BERT-medium | DeBERTa-XLarge | BERTScore  |
| moussaKam/frugalscore_tiny_bert-base_mover-score   | BERT-tiny   | BERT-base      | MoverScore |
| moussaKam/frugalscore_small_bert-base_mover-score  | BERT-small  | BERT-base      | MoverScore |
| moussaKam/frugalscore_medium_bert-base_mover-score | BERT-medium | BERT-base      | MoverScore |

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
