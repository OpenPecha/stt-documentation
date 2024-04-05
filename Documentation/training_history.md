
# Training history

The benchmark performance history on [openpecha/tibetan-voice-benchmark](https://huggingface.co/datasets/openpecha/tibetan-voice-benchmark) is bellow

|Model Name	|Model Type	|Benchmark mean CER	|STT_AB 	|STT_CS	|STT_MV	|STT_NS	|STT_TT|
|-----------|-----------|-------------------|-----------|-------|-------|-------|------|
|openpecha/wav2vec2_run8	    |wav2vec2	|27.01%	|4.09%	|41.45%	|42.05%	|27.43%	|14.73%|
|openpecha/wav2vec2_run9 ( 685 )|wav2vec2	|23.12%	|5.55%	|35.68%	|35.58%	|22.96%	|11.20%|
|spsither/wav2vec2_run9.640	    |wav2vec2	|23.19%	|5.51%	|35.79%	|35.86%	|23.00%	|23.00%|
|TenzinGayche/whisper-small-3	|whisper	|40.42%	|9.21%	|51.00%	|80.67%	|34.71%	|22.64%|

### openpecha/wav2vec2_run9

This training run was run on SageMaker Notebook instance of 
ml.g5.xlarge with 1 GPU, 24 GPU Memory, 4 vCPUs, 16 Memory
and had to be run for ~10 days.

The best performing model was found at step number 685000 where the eval/cer was 0.1987 and eval/loss 0.4468. Suprisingly the best performing checkpoint on benchmark was where eval/loss was minimum and not where eval/cer was min.

openpecha/wav2vec2_run9 got 23.12% CER on the openpecha/tibetan-voice-benchmark

### openpecha/wav2vec2_run10

Taking data snapshot at 4th April 2024. For 683.68 hours of data with the following distribution 

|Department | Hours      |
|-----------|------------|
|STT_AB     | 113.049924 |
|STT_CS     | 98.375647  |
|STT_MV     | 8.113259   |
|STT_NS     | 173.804951 |
|STT_PC     | 15.606155  |
|STT_TT     | 274.736280 |

Objective: compare the current facebook/wav2vec2-large-xlsr-53 with facebook/wav2vec2-xls-r-300m with the same data (till 4th April 2024). 
The datasets are in s3://monlam.ai.stt/dataset/wav2vec2/ 
The datasets there output of [prepare_dataset](https://github.com/OpenPecha/stt-wav2vec2/blob/main/prepare_dataset.ipynb) function. The same can be used for both the pretrained models.