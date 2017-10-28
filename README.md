# Webgrind

```yaml
version: '3'
services:

  php:
    image: php
    volumes:
      - "webgrind:/tmp/webgrind:rw"
    environment:
      XDEBUG_CONFIG: "profiler_output_dir=/tmp/webgrind"

  webgrind:
    container_name: webgrind
    image: tbfisher/webgrind
    environment:
      XDEBUG_OUTPUT_DIR: /tmp
      WEBGRIND_STORAGE_DIR: /tmp
      PHP_MAX_EXECUTION_TIME: 1200
      VIRTUAL_HOST: "webgrind.${LDEV_HOSTNAME}"
      VIRTUAL_PORT: "80"
      CERT_NAME: ssl-cert-snakeoil
    volumes:
      - "webgrind:/tmp:rw"

volumes:
  webgrind:
    driver: local
```
