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


## Access to the Filtron API

The [Filtron API](https://github.com/asciimoo/filtron#api) is available on ```http://localhost:4041```

For example, to display the loaded rules:
```
curl http://localhost:4041/rules | jq
```
