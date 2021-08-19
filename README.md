# nginx-proxy-compose

Docker Compose file with [nginx-proxy](https://github.com/nginx-proxy/nginx-proxy) and [acme-companion](https://github.com/nginx-proxy/acme-companion) to easily start a Nginx reverse proxy with SSL enabled.

## Usage

Clone this repository and clone the .env.example file:
```bash
$ git clone git@github.com:JoaoComini/nginx-proxy-compose.git
$ cp .env.example .env
```
And then change the environment variables inside `.env` file as you need.

Run it with `docker-compose`
```bash
$ docker-compose up -d
```

Start proxied containers
```bash
$ do
```

**Note:** all containers that will be proxied needs to run inside `nginx-proxy` docker network created by this compose file.

## Supported environment variables
- `NGINX_PROXY_IMAGE_TAG`: [nginx-proxy](https://github.com/nginx-proxy/nginx-proxy) docker image tag;
- `LETSENCRYPT_DEFAULT_EMAIL`: maps to `DEFAULT_EMAIL` variable from acme-companion, this email will be used by Let's Encrypt to warn about cetificates expiration.