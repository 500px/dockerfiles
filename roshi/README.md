# Roshi
A minimal Docker image to run [Roshi](https://github.com/soundcloud/roshi).

# `Dockerfile` links
* [latest](https://github.com/pwyliu/dockerfiles/blob/master/roshi/Dockerfile)


# What is Roshi?
[Roshi](https://github.com/soundcloud/roshi) implements a time-series event storage via a LWW-element-set CRDT with limited inline garbage collection. Roshi is a stateless, distributed layer on top of Redis and is implemented in Go. It is partition tolerant, highly available and eventually consistent.

Roshi is [super cool](https://developers.soundcloud.com/blog/roshi-a-crdt-system-for-timestamped-events).


# How To Use This Image
Roshi uses Redis as its persistence layer. You will need to have a Redis instance running somewhere for Roshi to connect to. A production installation of Roshi should have at least 3 independent Redis clusters running in different failure domains. For demo purposes you can just run Roshi on a single Redis instance with zero fault tolerance. See [the](https://github.com/soundcloud/roshi) [various](https://github.com/soundcloud/roshi/tree/master/roshi-server) [readme's](https://github.com/soundcloud/roshi/tree/master/farm) for more details.

![Roshi architecture](https://camo.githubusercontent.com/a58ab4eb770cc1429d291d77ced4cf5f88d9154f/687474703a2f2f692e696d6775722e636f6d2f5345654b7175572e706e67)

## Starting a Roshi instance

```
# Start a Redis instance named my-redis and daemonize
docker run --name my-redis -d redis

# Start a Roshi instance named my-roshi, linked to my-redis with an alias of redis_backend, exposing port 6302 to localhost
docker run --name my-roshi --link my-redis:redis_backend -p 6302:6302 roshi -redis.instances=redis_backend:6379

# In another shell you can curl /metrics to see that it's running
curl localhost:6302/metrics

# If you are using boot2docker
curl "$(boot2docker ip):6302/metrics"
```

This image includes `EXPOSE 6302` (the default roshi port), so container linking will work.

# Roshi License
View the [Roshi license information](https://github.com/soundcloud/roshi/blob/master/LICENSE.md).

## Contributing
Hey just [submit a PR](https://github.com/pwyliu/dockerfiles). Ain't no thang.
