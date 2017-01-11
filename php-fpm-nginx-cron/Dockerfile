FROM mountkin/php-nginx:7

RUN apt-get update && \
  apt-get install -y --no-install-recommends cron logrotate && \
  rm -fr /var/cache/apt /etc/logrotate.d/*

ADD cont-init.d/01-touch-crontab /etc/cont-init.d/
ADD services.d/cron/run /etc/services.d/cron/
ADD conf/logrotate.conf /etc/logrotate.d/web
RUN chmod 644 /etc/logrotate.d/web
ADD conf/zz-docker.conf /usr/local/etc/php-fpm.d/
ADD conf/nginx.conf /etc/nginx/
