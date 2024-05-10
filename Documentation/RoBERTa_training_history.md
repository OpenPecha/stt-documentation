# RoBERTa Training history

|Notebook Name  | num parameters | Instance      |Data   |Line merge | Tokenizer       | Vocab size | Train,val batch size | Tain,val split |
|---------------|----------------|---------------|-------|-----------|-----------------|------------|----------------------|----------------|
| gold-only     | 110m           | ml.g5.2xlarge | gold  | 6         | tokenizer_G     | 86761      | 16,16                | 1.9%           |
| test          | 166m           | ml.g5.4xlarge | A_f_d | 1         | tokenizer_A_f_d | 159159     | 24,24                | 11%            |
| RoBERTa-large | 416m           | ml.g5.4xlarge | A_f_d | 1         | tokenizer_A_f_d | 159159     | 24,24                | 11%            |
| sentencepiece | 84m            | ml.g5.12xlarge| A_S_c | 1         | tokenizer_S_b   | 52000      | 60,60                | 5%             |

# Tokenizers

|Tokenizer        | Data                                              | VOCAB_SIZE    | min_frequency | tokenizer.vocab_size| pre_tok   |
|-----------------|---------------------------------------------------|---------------|---------------|---------------------|-----------|
| tokenizer_A_f_d | spsither/tibetan_monolingual_A_filtered_deduped   | 256000        | 2             | 159159              | ByteLevel |
| tokenizer_S_a   | spsither/tibetan_monolingual_S_cleaned_train_test | 256000        | 2             | 121231              | ByteLevel |
| tokenizer_S_b   | spsither/tibetan_monolingual_S_cleaned_train_test | 52000         | 2             | 52000               | ByteLevel |
| tokenizer_S_c   | spsither/tibetan_monolingual_S_cleaned_train_test | 52000         | 2             | 52000               | Unigram   |
| tokenizer_S_d   | spsither/tibetan_monolingual_S_cleaned_train_test | 52000         | 2             | 52000               | Split     |
| tokenizer_S_e   | spsither/tibetan_monolingual_S_cleaned_train_test | 52000         | 3             | 52000               | ByteLevel |




### RoBERTa-large_v1

##### Objective
Get a MLM pretrained RoBERTa to be used for various downstream task.

##### Data used
18GB of [filtered deduped A data](https://huggingface.co/datasets/spsither/tibetan_monolingual_A_filtered_deduped)

##### Training Environment
Sagemaker notebook with `ml.g5.4xlarge`
Started at Apr 26th 4:50 PM

##### Hyperparameters
 - num_train_epochs = 50
 - learning_rate = 1e-4
 - warmup_steps = 500
 - weight_decay = 0.01
 - per_device_train_batch_size = 8
 - per_device_eval_batch_size  = 8
 - gradient_accumulation_steps = 1
 - gradient_checkpointing = True
 - fp16 = True
 - group_by_length = True
