# keras placeholder problem
## error message
```
tensorflow.python.framework.errors_impl.InvalidArgumentError: You must feed a value for placeholder tensor 'batch_normalization_1/keras_learning_phase' with dtype bool
         [[Node: batch_normalization_1/keras_learning_phase = Placeholder[dtype=DT_BOOL, shape=[], _device="/job:localhost/replica:0/task:0/gpu:0"]()]]
         [[Node: gradients/AddN_81/_487 = _Recv[client_terminated=false, recv_device="/job:localhost/replica:0/task:0/cpu:0", send_device="/job:localhost/replica:0/task:0/gpu:0", send_device_incarnation=1, tensor_name="edge_6518_gradients/AddN_81", tensor_type=DT_FLOAT, _device="/job:localhost/replica:0/task:0/cpu:0"]()]]
```

## solve
```python
from keras import backend as k
k.set_learning_phase(1)
```

## reference
[reference_website](<https://stackoverflow.com/questions/42969779/keras-error-you-must-feed-a-value-for-placeholder-tensor-bidirectional-1-keras>)
