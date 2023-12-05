# FT-Data-Ranker-1B-No.8
FT-Data-Ranker 1B赛道 第 8 名方案

# 核心思路
在 token 有限的情况下，句子越长且句子质量越高，喂进模型的训练效果越好。

# 训练流程

1. 产生训练数据集
```python
python ./data-juicer/tools/process_data.py --config ./juice_data_1119-2/alpaca-cot-en-refine.yaml

python ./lm-training/get_train_dataset_1b.py
```

2. 训练模型
```bash
bash ./lm-training/train_scripts/deepspeed_train_1b.sh \
    ./models/falcon-rw-1b \
    ./juice_data_1119-2/train_data_en.jsonl \
    ./res_1b_1119-2
```