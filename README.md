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
