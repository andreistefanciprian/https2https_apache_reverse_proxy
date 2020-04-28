
## Description

HTTP/HTTPS to HTTPS proxy with Debian Apache2

Enable HTTP or HTTPS for Apache frontend in frontend/Dockerfile:
```bash
# Start only HTTP page
# CMD ["apache2ctl", "-DFOREGROUND"]

# Start HTTPS page
CMD ["apache2ctl", "-DFOREGROUND", "-DSSL-ON"]
```

## Prerequisites

Have ssl certs in ssl/ folder.

## Build setup

```bash
# build container with docker compose
VERSION=4.28.2 docker-compose up -d --build


```

## Tests

```bash
# test apache reverse proxy
while true; do curl -k https://localhost:8443/; sleep 0.5; echo \n; done
while true; do curl -k http://localhost:80/; sleep 0.5; echo \n; done

# check container logs
docker container logs -f frontend
docker container logs -f backend
```

# Cleanup

```bash
VERSION=4.28.2 docker-compose down
```