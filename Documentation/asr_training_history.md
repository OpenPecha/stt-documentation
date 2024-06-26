
# ASR Training history

The benchmark performance history on [openpecha/tibetan-voice-benchmark](https://huggingface.co/datasets/openpecha/tibetan-voice-benchmark) is bellow

|Model Name	| Model Type          |Benchmark mean CER |STT_AB | STT_CS | STT_MV | STT_NS | STT_TT |
|-----------|---------------------|-------------------|-------|--------|--------|--------|--------|
| spsither/mms_300_v3.1020*       | mms_300  | 18.16% | 4.05% | 33.11% | 18.03% | 21.70% |  8.39% |
| spsither/mms_300_v3.800*        | mms_300  | 18.45% | 4.30% | 33.74% | 18.27% | 21.88% |  8.43% |
| spsither/mms_300_v3.800         | mms_300  | 19.54% | 4.83% | 34.59% | 19.08% | 23.04% | 10.61% |
| openpecha/tibetan_asr_mms300_v1 | mms_300  | 19.89% | 4.71% | 33.63% | 24.72% | 21.90% |  9.44% |
| spsither/mms_300_v2.1190        | mms_300  | 20.26% | 4.63% | 34.84% | 24.94% | 22.21% |  9.37% |
| spsither/mms_300_v1.780         | mms_300  | 20.29% | 4.63% | 34.09% | 25.70% | 22.21% |  9.75% |
| openpecha/wav2vec2_run10        | wav2vec2 | 20.42% | 4.78% | 34.42% | 25.86% | 22.21% |  9.72% |
| spsither/mms_300_v1.630         | mms_300  | 20.50% | 5.32% | 34.36% | 25.68% | 22.15% |  9.92% |
| spsither/wav2vec2_run10.1055    | wav2vec2 | 20.55% | 4.73% | 34.57% | 26.44% | 22.08% |  9.79% |
| spsither/wav2vec2_run10.950     | wav2vec2 | 20.61% | 4.74% | 34.52% | 26.42% | 22.30% |  9.95% |
| spsither/wav2vec2_run10.855     | wav2vec2 | 20.76% | 5.12% | 34.63% | 26.81% | 22.26% |  9.91% |
| spsither/wav2vec2_run10.840     | wav2vec2 | 20.77% | 4.80% | 34.65% | 26.96% | 22.29% | 10.05% |
| spsither/wav2vec2_run10.660     | wav2vec2 | 21.18% | 5.35% | 35.13% | 27.37% | 22.62% | 10.32% |
| spsither/wav2vec2_run10.605     | wav2vec2 | 21.26% | 5.36% | 35.59% | 27.40% | 22.48% | 10.22% |
| openpecha/wav2vec2_run8	      | wav2vec2 | 27.01% | 4.09% | 41.45% | 42.05% | 27.43% | 14.73% |
| openpecha/wav2vec2_run9         | wav2vec2 | 23.12% | 5.55% | 35.68% | 35.58% | 22.96% | 11.20% |
| spsither/wav2vec2_run9.640      | wav2vec2 | 23.19% | 5.51% | 35.79% | 35.86% | 23.00% | 23.00% |
| TenzinGayche/whisper-small-3    | whisper  | 40.42% | 9.21% | 51.00% | 80.67% | 34.71% | 22.64% |

\* evaluate after normalizing shae to tsag

### openpecha/wav2vec2_run9

##### Hyperparameters
 - per_device_train_batch_size=16
 - gradient_accumulation_steps=1
 - num_train_epochs=25
 - fp16=True
 - learning_rate=3e-5
 - warmup_steps=500

##### Training Environment
This training run was run on SageMaker Notebook instance of 
ml.g5.xlarge with 1 GPU, 24 GPU Memory, 4 vCPUs, 16 Memory
and had to be run for ~10 days.

##### Checkpoint selection
The best performing model was found at step number 685000 where the eval/cer was 0.1987 and eval/loss 0.4468. Suprisingly the best performing checkpoint on benchmark was where eval/loss was minimum and not where eval/cer was min.

openpecha/wav2vec2_run9 got 23.12% CER on the openpecha/tibetan-voice-benchmark. This checkpoint was taken at step 685000.

### openpecha/wav2vec2_run10

##### Objective
Compare the current `facebook/wav2vec2-large-xlsr-53` with `facebook/wav2vec2-xls-r-300m` with the same data (till 4th April 2024). 
The datasets are in s3://monlam.ai.stt/dataset/wav2vec2/ 
The datasets there output of [prepare_dataset](https://github.com/OpenPecha/stt-wav2vec2/blob/main/prepare_dataset.ipynb) function. The same can be used for both the pretrained models.

##### Data used
Taking data snapshot at 4th April 2024. For 683.68 hours of data with the following distribution 

|Department | Hours      |
|-----------|------------|
|STT_AB     | 113.049924 |
|STT_CS     | 98.375647  |
|STT_MV     | 8.113259   |
|STT_NS     | 173.804951 |
|STT_PC     | 15.606155  |
|STT_TT     | 274.736280 |

##### Training Environment
This wav trained at local computer with the following spec
- GPU: NVIDIA GeForce RTX 4090/PCIe/SSE2 / NVIDIA Corporation
- CPU: AMD® Ryzen 9 7900 12-core processor × 24
- RAM: 64.0 GiB

The model was trained for about ~8 days

##### Hyperparameters
 - per_device_train_batch_size=8
 - gradient_accumulation_steps=2
 - num_train_epochs=40
 - fp16=True
 - learning_rate=3e-5
 - warmup_steps=500

##### Checkpoint selection
The model at step 1340000 has eval/loss of 0.4124. This checkpoint was pushed as openpecha/wav2vec2_run10 to HuggingFace.

### openpecha/tibetan_asr_mms300_v1

This model was trained on the same environment, data and hyperparameters as openpecha/wav2vec2_run10. Started the training on Apr 15th.
Training stopped at Apr 23rd. It ran for 36.4 epochs. The model learns faster but when trained for long enough `facebook/wav2vec2-large-xlsr-53` gives similar results.

The model was trained for about ~8 days. openpecha/tibetan_asr_mms300_v1 was at step 900000.

### openpecha/tibetan_asr_mms300_v2

##### Objective
Traine with and without freezing the feature extractor `model.freeze_feature_extractor()` and see the effects.

##### Data used
Taking data snapshot at 23rd April 2024. For 771.30 hours of data with the following distribution.

|Department | Hours  |
|-----------|--------|
|STT_AB     | 130.82 |
|STT_CS     | 109.24 |
|STT_MV     | 32.60  |
|STT_NS     | 191.96 |
|STT_PC     | 21.94  |
|STT_TT     | 284.75 |

Training started on Apr 23rd evening. Stopped on Apr 30rd noon.

##### Checkpoint selection
Checkpoint at step 1190000 pushed to HF.

### openpecha/tibetan_asr_mms300_v3

##### Data used
Taking data snapshot at 24th may 2024. For 1006.15 hours of data with the following distribution.

|Department | Hours  |
|-----------|--------|
|STT_AB     | 145.65 |
|STT_CS     | 123.58 |
|STT_HS     | 2.35   |
|STT_MV     | 162.84 |
|STT_NS     | 203.44 |
|STT_NW     | 34.79  |
|STT_PC     | 33.26  |
|STT_TT     | 300.25 |

Training started on May 30th. spsither/mms_300_v3.1020 has lowest val loss so far.