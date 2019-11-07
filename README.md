The project is forked from: https://github.com/oliver006/redis_exporter

Modified it to support redis sentinel.

Add flags:

Name                   | Environment Variable Name            | Description
-----------------------|--------------------------------------|-----------------
sentinel.addrs             | SENTINEL_ADDRS                           | Address of the Redis sentinels spilt by ',', defaults to `localhost:26379`.
redis.master         | REDIS_MASTER                       | Redis master name the sentinels monitoring, defaults to `mymaster`.

And the flag redis.addr was ignored.

When every scrape request arrives, it will trying to find redis master address by sentinel.addrs and redis.master by command `sentinel get-master-addr-by-name <masterName>`, and then process as before with redis master address as redis.addr.
