## msgpack Problem

- when using airsim api, and establish a client, msgpack error occur

### code 
```python
import airsim

client = airsim.MultirotorClient()
client.confirmConnection()
```



### error message
```
Traceback (most recent call last):
  File "test_rollyawpitch.py", line 13, in <module>
    client.confirmConnection()
  File "C:\Users\ZONGC\Anaconda3\envs\airsim2\lib\site-packages\airsim\client.py", line 139, in confirmConnection
    if self.ping():
  File "C:\Users\ZONGC\Anaconda3\envs\airsim2\lib\site-packages\airsim\client.py", line 44, in ping
    return self.client.call("ping")
  File "C:\Users\ZONGC\Anaconda3\envs\airsim2\lib\site-packages\msgpackrpc\session.py", line 41, in call
    return self.send_request(method, args).get()
  File "C:\Users\ZONGC\Anaconda3\envs\airsim2\lib\site-packages\msgpackrpc\session.py", line 51, in send_request
    self._transport.send_message([message.REQUEST, msgid, method, args])
  File "C:\Users\ZONGC\Anaconda3\envs\airsim2\lib\site-packages\msgpackrpc\transport\tcp.py", line 89, in send_message
    self.connect()
  File "C:\Users\ZONGC\Anaconda3\envs\airsim2\lib\site-packages\msgpackrpc\transport\tcp.py", line 98, in connect
    socket = ClientSocket(stream, self, self._encodings)
  File "C:\Users\ZONGC\Anaconda3\envs\airsim2\lib\site-packages\msgpackrpc\transport\tcp.py", line 53, in __init__
    BaseSocket.__init__(self, stream, encodings)
  File "C:\Users\ZONGC\Anaconda3\envs\airsim2\lib\site-packages\msgpackrpc\transport\tcp.py", line 12, in __init__
    self._packer = msgpack.Packer(encoding=encodings[0], default=lambda x: x.to_msgpack())
  File "msgpack\_packer.pyx", line 124, in msgpack._cmsgpack.Packer.__init__
TypeError: __init__() got an unexpected keyword argument 'encoding'
```

### Solve
`pip uninstall airsim`
`pip uninstall msgpack`
`pip uninstall msgpack-python`
`pip uninstall msgpack-rpc-python`
then follow the [docs](https://microsoft.github.io/AirSim/apis/) and reinstall the `airsim` and `msgpack-rpc-python` packages

### Reference
