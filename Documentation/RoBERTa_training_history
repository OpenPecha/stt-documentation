# RoBERTa Training history

|Notebook Name  | num parameters | Instance      |Data  |Line merge | Vocab size | Train,val batch size | Tain,val split |
|---------------|----------------|---------------|------|-----------|------------|----------------------|----------------|
| gold-only     | 110m           | ml.g5.2xlarge | gold | 6         | 86761      | 16,16                | 1.9%           |
| test          | 83m            | ml.g5.4xlarge | A    | 7         | 52000      | 24,20                | 5.1%           |
| RoBERTa-large | 342m           | ml.g5.4xlarge | gold | 1,3,5     | 86761      | 24,24                | 1.9%           |


### RoBERTa-large

##### Hyperparameters
 - num_train_epochs = 50
 - learning_rate = 1e-4
 - warmup_steps = 500
 - weight_decay = 0.01
 - per_device_train_batch_size = 24
 - per_device_eval_batch_size  = 24
 - gradient_checkpointing = True
 - fp16 = True
 - gradient_accumulation_steps = 2
 - group_by_length = True
