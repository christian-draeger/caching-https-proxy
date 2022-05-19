# caching-https-proxy

## Why

tbd

### How it works

tbd

### Usage
#### Configuration via environment variables

| **Env Var**              | **default value** | **description**                                                                                                                                                                                                                                                                                                                                                                                                               |
|--------------------------|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| EXTERNAL_HOST            | github.com        | The host name you want to cache calls to.                                                                                                                                                                                                                                                                                                                                                                                     |
| PORT                     | 8080              | The internal Port of the Proxy                                                                                                                                                                                                                                                                                                                                                                                                |
| ROUTE                    | /                 | Used route prefix.                                                                                                                                                                                                                                                                                                                                                                                                            |
| CACHE_PATH               | /tmp/cache        | The local disk directory where the cached resources a saved.                                                                                                                                                                                                                                                                                                                                                                  |
| CACHE_KEY_ZONE_SIZE      | 10m               | keys_zone sets up a shared memory zone for storing the cache keys and metadata such as usage timers. Having a copy of the keys in memory enables the caching-https-proxy to quickly determine if a request is a HIT or a MISS without having to go to disk, greatly speeding up the check. A 1‑MB zone can store data for about 8,000 keys, so the 10‑MB zone configured in the example can store data for about 80,000 keys. |
| CACHE_MAX_SIZE           | 1g                | Sets the upper limit of the size of the cache. When the cache size reaches the limit, a process called the cache manager removes the files that were least recently used to bring the cache size back under the limit.                                                                                                                                                                                                        |
| CACHE_ENTRY_INACTIVE_TTL | 72h               | Evict least recently used entries (entries without a cache hit) after a given time.                                                                                                                                                                                                                                                                                                                                           |
| CACHE_ENTRY_ACTIVE_TTL   | 30d               | Evict entries older than a given time.                                                                                                                                                                                                                                                                                                                                                                                        |

### Deployment

tbd: want to provide helm chart to convenient deploy to k8s as well as heroku deployment.

### Development

To build the caching-https-proxy docker image on your local machine run following command from projects root:
```shell
docker build -t caching-https-proxy:latest ./source
```

run local docker image on a given host machines port (e.g. 8000):
```shell
docker run -p 8000:8080 caching-https-proxy
```

ssh into running container:
```shell
docker exec -it <container-id> /bin/sh
```
