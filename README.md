# Webgrind

[Webgrind](https://github.com/jokkedk/webgrind) docker image.

To get this to show your xdebug profiler dumps:

1. Install xdebug, [enable profiling](https://xdebug.org/docs/profiler) in your php container.
2. Share your php container `profiler_output_dir` via a docker volume with `/tmp` in the webgrind container.

See [`docker-compose.yml`](docker-compose.yml):

```bash
docker-compose up -d
# this enables xdebug in my php container
docker-compose exec php /bin/bash -c 'sed -i "s/^;//" /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini; kill -USR2 1'

# open http://localhost/ to trigger profile
# open http://localhost:8080/ to view the profile

# clean up
docker-compose down -v
```
