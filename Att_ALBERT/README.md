ALBERT+MA
======

GLUE
====================
example：

```
pip install -r albert/requirements.txt
python -m albert.run_classifier \
  --data_dir=... \
  --output_dir=... \
  --init_checkpoint=... \
  --albert_config_file=... \
  --spm_model_file=... \
  --do_train \
  --do_eval \
  --do_predict \
  --do_lower_case \
  --max_seq_length=128 \
  --optimizer=adamw \
  --task_name=MNLI \
  --warmup_step=1000 \
  --learning_rate=2e-5 \
  --train_step=10000 \
  --save_checkpoints_steps=100 \
  --train_batch_size=128
```


SQuADv1.1
====================
example：

```
pip install -r albert/requirements.txt
python -m albert.run_squad_v1 \
  --albert_config_file=... \
  --output_dir=... \
  --train_file=... \
  --predict_file=... \
  --train_feature_file=... \
  --predict_feature_file=... \
  --predict_feature_left_file=... \
  --init_checkpoint=... \
  --spm_model_file=... \
  --do_lower_case \
  --max_seq_length=384 \
  --doc_stride=128 \
  --max_query_length=64 \
  --do_train=true \
  --do_predict=true \
  --train_batch_size=48 \
  --predict_batch_size=8 \
  --learning_rate=2e-5 \
  --num_train_epochs=3.0 \
  --warmup_proportion=.1 \
  --save_checkpoints_steps=5000 \
  --n_best_size=20 \
  --max_answer_length=30
```


SQuADv2.0
====================
example：
```
pip install -r albert/requirements.txt
python -m albert.run_squad_v2 \
  --albert_config_file=... \
  --output_dir=... \
  --train_file=... \
  --predict_file=... \
  --train_feature_file=... \
  --predict_feature_file=... \
  --predict_feature_left_file=... \
  --init_checkpoint=... \
  --spm_model_file=... \
  --do_lower_case \
  --max_seq_length=384 \
  --doc_stride=128 \
  --max_query_length=64 \
  --do_train \
  --do_predict \
  --train_batch_size=48 \
  --predict_batch_size=8 \
  --learning_rate=2e-5 \
  --num_train_epochs=3.0 \
  --warmup_proportion=.1 \
  --save_checkpoints_steps=5000 \
  --n_best_size=20 \
  --max_answer_length=30
```

You can fine-tune the model starting from TF-Hub modules instead of raw
checkpoints by setting e.g.
`--albert_hub_module_handle=https://tfhub.dev/google/albert_base/1` instead
of `--init_checkpoint`.

RACE
===================
example：

```
pip install -r albert/requirements.txt
python -m albert.run_race \
  --albert_config_file=... \
  --output_dir=... \
  --train_file=... \
  --eval_file=... \
  --data_dir=...\
  --init_checkpoint=... \
  --spm_model_file=... \
  --max_seq_length=512 \
  --max_qa_length=128 \
  --do_train \
  --do_eval \
  --train_batch_size=16 \
  --eval_batch_size=8 \
  --learning_rate=2e-5 \
  --train_step=12000 \
  --warmup_step=1000 \
  --save_checkpoints_steps=100
```

You can fine-tune the model starting from TF-Hub modules instead of raw
checkpoints by setting e.g.
`--albert_hub_module_handle=https://tfhub.dev/google/albert_base/1` instead
of `--init_checkpoint`.
