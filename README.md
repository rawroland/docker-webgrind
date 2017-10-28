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
    volumes:
      - "webgrind:/tmp:rw"

volumes:
  webgrind:
    driver: local
```
