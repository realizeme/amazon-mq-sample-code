amazon-mq sample code
===============================

version number: 0.0.1
author: hyunsung.kim

Overview
--------

There is no clue when we try to use amazon mq with python which is actually active mq, so here I add some python sample code.

In sample code, you can see unidirectional or bidirectional(a.k.a RPC) sample source code.


Installation / Usage
--------------------

To install use pip:

    $ pip install stomp.py==4.1.19
    

Example
-------

```python
from stompest.config import StompConfig
from stompest.sync import Stomp
import ssl

context = ssl.create_default_context()
# Disable cert validation for demo only
context.check_hostname = False
context.verify_mode = ssl.CERT_NONE

CONFIG = StompConfig(uri='ssl://x.x.x.x:61614', login='id', passcode='password', check=False, sslContext=context)
QUEUE = '/queue/my-queue'

if __name__ == '__main__':
    client = Stomp(CONFIG)
    client.connect()
    client.send(QUEUE, 'test message 1'.encode())
    client.send(QUEUE, 'test message 2'.encode())
    client.disconnect()
```