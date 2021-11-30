# FrugalScore
FrugalScore is an approach to learn a fixed, low cost version of any expensive NLG metric, while retaining most of its original performance

Paper: https://arxiv.org/abs/2110.08559?context=cs

The pretrained checkpoints presented in the paper can be found on the [huggingface models hub](https://huggingface.co/moussaKam)

You can run the example by using the following command:

```
python run_glue.py \
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
pip install datasets
pip install git+https://github.com/huggingface/transformers
```
