# Searx stack for Portainer

Create a new searx instance in five minutes using [Portainer](https://www.portainer.io/)

## What is included ?

| Name | Description | Docker image | Dockerfile |
| -- | -- | -- | -- |
| [Nginx](https://www.nginx.com/) | Reverse proxy http server | [nginx:latest](https://hub.docker.com/_/nginx) | [Dockerfile](https://www.nginx.com/) |
| [Filtron](https://github.com/asciimoo/filtron) |  Filtering reverse HTTP proxy, bot and abuse protection | [dalf/filtron:latest](https://hub.docker.com/r/dalf/filtron) | See [asciimoo/filtron#4](https://github.com/asciimoo/filtron/pull/4) |
| [Searx](https://github.com/asciimoo/searx) | searx by itself | [searx/searx:latest](https://hub.docker.com/r/searx/searx) | [Dockerfile](https://github.com/searx/searx/blob/master/Dockerfile) |
| [Morty](https://github.com/asciimoo/morty) | Privacy aware web content sanitizer proxy as a service. | [dalf/morty:latest](https://hub.docker.com/r/dalf/morty) | [Dockerfile](https://github.com/dalf/morty/blob/master/Dockerfile) |

## How to use it
- [Install docker](https://docs.docker.com/install/)
- [Install docker-compose](https://docs.docker.com/compose/install/) (be sure that docker-compose version is at least 1.9.0).
- [Install Portainer](https://docs.portainer.io/v/ce-2.9/start/install)
- Use the stack GUI to spawn your Searx instance

## Environment variables
```
# Repository container the nginx templates and other configurations
CONFIG_REPO_URL=https://github.com/oleduc/searx-docker-portainer.git

# Example search.example.com or localhost (default)
SEARX_HOSTNAME=<hostname>

# use openssl rand -base64 33
MORTY_KEY=<key>

# NGINX HTTP port
NGINX_HTTP_PORT=5080
# NGINX HTTPS port
NGINX_HTTPS_PORT=5443
# Path to your ssl certificates
SSL_CERT_PATH=<path to your fullchain certificate>
SSL_KEY_PATH=<path to your private key>

# Nginx static assests cache configuratio
# Size of the cached file index
STATIC_CACHE_INDEX_SIZE=64m
# Maximum total size of the cached assets
STATIC_SERVER_CACHE_MAX_SIZE=1024m
# How long until an asset is considered expired
STATIC_CACHE_EXPIRATION=30d
# How long after expiration is an asset deleted
STATIC_CACHE_INACTIVE=1d
# How long should the client cache the request response
STATIC_CLIENT_CACHE_MAX_AGE=2592000


# Size of the cached search results index
RESULTS_CACHE_INDEX_SIZE=256m
# Maximum total size of the cache
RESULTS_SERVER_CACHE_MAX_SIZE=5120m
# How long until a search result is considered expired
RESULTS_CACHE_EXPIRATION=10m
# How long after expiration is a result deleted
RESULTS_CACHE_INACTIVE=5m
# How long should the client cache the request response
RESULTS_CLIENT_CACHE_MAX_AGE=600
```
## Access to the Filtron API

The [Filtron API](https://github.com/asciimoo/filtron#api) is available on ```http://localhost:4041```

For example, to display the loaded rules:
```
curl http://localhost:4041/rules | jq
```
