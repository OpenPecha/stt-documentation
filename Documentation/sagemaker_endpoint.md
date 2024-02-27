# SageMaker Endpoint

## Comparison of HuggingFace Inference Endpoint vs SageMaker Endpoint

For a given specification of
- HuggingFace 
(GPU · Nvidia Tesla T4 · 1x GPU · 16 GB) and comparable instance on 
- SageMaker `ml.g4dn.xlarge` (GPU · Nvidia T4 · 1x GPU · 16 GB · 4 vCPU · 16 RAM) 

The cost per hour are 
- $0.60 on HuggingFace and 
- $0.7364 on SageMaker

The upperlimit on audio length till they threw CUDA out of memory was 
- 195 seconds was the best I could make a request on SageMaker till the following error 

```
CUDA out of memory. Tried to allocate 5.96 GiB. GPU 0 has a total capacty of 14.76 GiB of which 5.68 GiB is free. Process 9533 has 9.08 GiB memory in use. Of the allocated memory 7.46 GiB is allocated by PyTorch, and 646.60 MiB is reserved by PyTorch but unallocated. If reserved but unallocated memory is large try setting max_split_size_mb to avoid fragmentation.  See documentation for Memory Management and PYTORCH_CUDA_ALLOC_CONF
```

- 155 seconds was the longest I could run on HuggingFace till this error 
```
CUDA out of memory. Tried to allocate 3.81 GiB (GPU 0; 14.58 GiB total capacity; 5.28 GiB already allocated; 3.63 GiB free; 10.58 GiB reserved in total by PyTorch) If reserved memory is >> allocated memory try setting max_split_size_mb to avoid fragmentation.  See documentation for Memory Management and PYTORCH_CUDA_ALLOC_CONF
```

If using API Gateway and Lambda to run the SageMaker inference the largest audio length I could POST was 145 seconds before getting 413 Request Entity Too Long error. Thus using S3 URL to transfer the file is better.