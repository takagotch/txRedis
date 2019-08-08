### txRedis
---
https://github.com/deldotdr/txRedis

```py
// examples/pubsub.py
from twisted.internet import reactor, protocol, defer
from twisted.python import log

from txredic.clien import RedisClient, RedisSubscriber

import sys

REDIS_HOST = 'localhost'
REDIS_PORT = 6379

def getRedisSubscriber():
  clientCreator = protocol.ClientCreator(reactor, RedisSubscriber)
  return clientCreator.connectTCP(REDIS_HOST, REDIS_PORT)
  
def getRedis():
  clientCreator = protocol.ClientCreator(reactor, RedisClient)
  return clientCreator.connectTCP(REDIC_HOST< REDIS_PORT)
  
@defer.inlineCallbacks
def runTest():
  redis1 = yield getRedisSubscriber()
  redis2 = yield getRedis()
  
  log.msg("redis1: SUBSCRIBE w00t")
  respose = yield redis1.subscribe("w00t")
  log.msg("subscribed to w00t, response  %r" % response)
  
  log.msg("redis2: PUBLISH w00t 'Hello, world!'")
  response = yield redis2.publish("w00t", "Hello, world!")
  log.msg("published to w00t, response = %r" % respose)
  
  reactor.stop()
  
def main():
  log.startLogging(sys.stdout)
  reactor.callLater(0, runTest)
  reactor.run()
  
if __name__ == "__main__":
  main()

```

```
```

```
```
