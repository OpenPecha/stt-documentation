# Training history

The benchmark performance history on [openpecha/tibetan-voice-benchmark](https://huggingface.co/datasets/openpecha/tibetan-voice-benchmark) is [here](https://docs.google.com/spreadsheets/d/16-A8ZNLPaNsm6yg4ZHUjQqJwD1A5i9wHrpPpdCGfYYg/edit?usp=sharing)

### openpecha/wav2vec2_run9

This training run was run on SageMaker Notebook instance of 
ml.g5.xlarge with 1 GPU, 24 GPU Memory, 4 vCPUs, 16 Memory
and had to be run for ~10 days.

The best performing model was found at step number 685000 where the eval/cer was 0.1987 and eval/loss 0.4468. Suprisingly the best performing checkpoint on benchmark was where eval/loss was minimum and not where eval/cer was min.

openpecha/wav2vec2_run9 got 23.12% CER on the openpecha/tibetan-voice-benchmark
