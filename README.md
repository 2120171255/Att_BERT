# Att_BERT


### Att_BERT and Att_ALBERT: multiway attention networks for sentence representation.


### Rusult on GLUE dataset:
|Model|MNLI-(m/mm)|QQP|QNLI|SST-2 |CoLA|STS-B |MRPC|RTE|Average|
|-|-|-|-|-|-|-|-|-|-|
|BERT-base|84.1/83.4|71.1|90.5|92.6|52.1|85.8|88.9|66.4|79.4|
|Att-BERT|84.0/83.6|71.0|91.1|93.2|54.5|86.2|89.9|69.5|80.3|
|ALBERT-base|83.7/82.5|70.9|91.1|92.6|57.1|88.4|89.5|70.6|80.7|
|Att-ALBERT|84.0/83.4|71.0|91.8|93.7|57.1|88.5|90.2|71.3|81.2|


### Rusult on SQuAD and RACE dataset:
||SQuADv1.1|SQuADv2.0|RACE|
|-|-|-|-|
|BERT-base|88.5|76.9|-|
|Att-BERT|88.8|77.3|-|
|ALBERT-base|89.9|81.3|66.8|
|Att-ALBERT|90.2|81.8|70.7|


# BERT+MA

```

### Sentence (and sentence-pair) classification tasks

example：

```shell
export BERT_BASE_DIR=/path/to/bert/uncased_L-12_H-768_A-12
export GLUE_DIR=/path/to/glue

python run_classifier.py \
  --task_name=MRPC \
  --do_train=true \
  --do_eval=true \
  --data_dir=$GLUE_DIR/MRPC \
  --vocab_file=$BERT_BASE_DIR/vocab.txt \
  --bert_config_file=$BERT_BASE_DIR/bert_config.json \
  --init_checkpoint=$BERT_BASE_DIR/bert_model.ckpt \
  --max_seq_length=128 \
  --train_batch_size=32 \
  --learning_rate=2e-5 \
  --num_train_epochs=3.0 \
  --output_dir=/tmp/mrpc_output/
```


#### Prediction from classifier

example：

```shell
export BERT_BASE_DIR=/path/to/bert/uncased_L-12_H-768_A-12
export GLUE_DIR=/path/to/glue
export TRAINED_CLASSIFIER=/path/to/fine/tuned/classifier

python run_classifier.py \
  --task_name=MRPC \
  --do_predict=true \
  --data_dir=$GLUE_DIR/MRPC \
  --vocab_file=$BERT_BASE_DIR/vocab.txt \
  --bert_config_file=$BERT_BASE_DIR/bert_config.json \
  --init_checkpoint=$TRAINED_CLASSIFIER \
  --max_seq_length=128 \
  --output_dir=/tmp/mrpc_output/
```

### SQuAD 1.1

example：

```shell
python run_squad.py \
  --vocab_file=$BERT_LARGE_DIR/vocab.txt \
  --bert_config_file=$BERT_LARGE_DIR/bert_config.json \
  --init_checkpoint=$BERT_LARGE_DIR/bert_model.ckpt \
  --do_train=True \
  --train_file=$SQUAD_DIR/train-v1.1.json \
  --do_predict=True \
  --predict_file=$SQUAD_DIR/dev-v1.1.json \
  --train_batch_size=16 \
  --learning_rate=2e-5 \
  --num_train_epochs=3.0 \
  --max_seq_length=384 \
  --doc_stride=128 \
  --output_dir=gs://some_bucket/squad_large/ \
  --use_tpu=True \
  --tpu_name=$TPU_NAME
```


### SQuAD 2.0

example：

```shell
python run_squad.py \
  --vocab_file=$BERT_LARGE_DIR/vocab.txt \
  --bert_config_file=$BERT_LARGE_DIR/bert_config.json \
  --init_checkpoint=$BERT_LARGE_DIR/bert_model.ckpt \
  --do_train=False \
  --train_file=$SQUAD_DIR/train-v2.0.json \
  --do_predict=True \
  --predict_file=$SQUAD_DIR/dev-v2.0.json \
  --train_batch_size=24 \
  --learning_rate=3e-5 \
  --num_train_epochs=2.0 \
  --max_seq_length=384 \
  --doc_stride=128 \
  --output_dir=gs://some_bucket/squad_large/ \
  --use_tpu=True \
  --tpu_name=$TPU_NAME \
  --version_2_with_negative=True \
  --null_score_diff_threshold=$THRESH
```

