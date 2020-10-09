# TensorFLow-gpu Problem

## training using tensorflow-gpu: keras with cudnn problem

## Description
- cudnn install: done
- LD_LIBRARY_PATH setting: done
- when training, print out error message 

## Error Message:
```
E tensorflow/stream_executor/cuda/cuda_dnn.cc:329] Could not create cudnn handle: CUDNN_STATUS_INTERNAL_ERROR2020-01-16 00:25:55.901231: 
E tensorflow/stream_executor/cuda/cuda_dnn.cc:329] Could not create cudnn handle: CUDNN_STATUS_INTERNAL_ERROR2020-01-16 00:25:55.901300: W tensorflow/core/common_runtime/base_collective_executor.cc:216] BaseCollectiveExecutor::StartAbort Unknown: Failed to get convolution algorithm. 
This is probably because cuDNN failed to initialize, so try looking to see if a warning log message was printed above.
```



## Reference
[github Issue](<https://github.com/tensorflow/tensorflow/issues/24496>)
