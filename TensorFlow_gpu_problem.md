# TensorFLow-gpu Problem

<br>

## training using tensorflow-gpu: keras with cudnn problem

<br>

## Description
- cudnn install: done
- LD_LIBRARY_PATH setting: done
- when training, print out error message 

<br>

## Error Message:
```
E tensorflow/stream_executor/cuda/cuda_dnn.cc:329] Could not create cudnn handle: CUDNN_STATUS_INTERNAL_ERROR2020-01-16 00:25:55.901231: 
E tensorflow/stream_executor/cuda/cuda_dnn.cc:329] Could not create cudnn handle: CUDNN_STATUS_INTERNAL_ERROR2020-01-16 00:25:55.901300: W tensorflow/core/common_runtime/base_collective_executor.cc:216] BaseCollectiveExecutor::StartAbort Unknown: Failed to get convolution algorithm. 
This is probably because cuDNN failed to initialize, so try looking to see if a warning log message was printed above.
```

## How to solve:
- add this code at the beginning of the `training.py`(or `main.py`)
- ```python
  ## for tensorflow 1.x
  import tensorflow as tf
  config = tf.ConfigProto()
  config.gpu_options.allow_growth = True
  session = tf.InteractiveSession(config=config)
  ```

- ```python
  ## for tensorflow 2.x
  import tensorflow as tf 
  config = tf.compat.v1.ConfigProto()
  config.gpu_options.allow_growth = True
  session = tf.compat.v1.InteractiveSession(config=config)
  ```



<br>

## Reference
[github Issue](<https://github.com/tensorflow/tensorflow/issues/24496>)
[chinese reference](<https://mc.ai/%E4%BD%BF%E7%94%A8tensorflow-gpu-%E8%A8%93%E7%B7%B4keras%E7%84%A1%E6%B3%95%E5%95%9F%E7%94%A8cudnn%E7%9A%84%E5%95%8F%E9%A1%8C/>)
