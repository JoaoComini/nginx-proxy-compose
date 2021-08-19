# nginx-proxy-compose

Docker Compose file with [nginx-proxy](https://github.com/nginx-proxy/nginx-proxy) and [acme-companion](https://github.com/nginx-proxy/acme-companion) to easily start a Nginx reverse proxy with SSL enabled.

## Usage

Clone this repository and clone the `.env.example` file:
```bash
$ git clone git@github.com:JoaoComini/nginx-proxy-compose.git
$ cp .env.example .env
```
Then change the environment variables inside `.env` file as you need.

Run it with `docker-compose`:
```bash
$ docker-compose up -d --build
```

Start proxied containers:
```bash
$ docker run -dit --expose 80 \
    -e VIRTUAL_HOST=foo.local \
    -e LETSENCRYPT_HOST=foo.local \
    --network nginx-proxy \
    httpd:alpine
```

Be happy :)
```bash
$ curl -H 'Host: foo.local' localhost
<html><body><h1>It works!</h1></body></html>
```

**Note:** all containers that will be proxied needs to run inside `nginx-proxy` docker network created by this compose file.

## Supported environment variables
- `NGINX_PROXY_IMAGE_TAG`: [nginx-proxy](https://github.com/nginx-proxy/nginx-proxy) docker image tag;
- `LETSENCRYPT_DEFAULT_EMAIL`: maps to `DEFAULT_EMAIL` variable from [acme-companion](https://github.com/nginx-proxy/acme-companion), this email will be used by Let's Encrypt to warn about cetificates expiration.

---

For more information about proxied containers configuration, please visit [nginx-proxy](https://github.com/nginx-proxy/nginx-proxy) and [acme-companion](https://github.com/nginx-proxy/acme-companion).
