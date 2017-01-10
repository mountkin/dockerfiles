FROM mountkin/php-nginx:7

RUN apt-get update && \
  apt-get install -y --no-install-recommends cron logrotate && \
  rm -fr /var/cache/apt /etc/logrotate.d/*

RUN sed -i '/global/a pid = /var/run/php-fpm.pid' /usr/local/etc/php-fpm.d/zz-docker.conf

ADD services.d/cron/run /etc/services.d/cron/
ADD conf/logrotate.conf /etc/logrotate.d/web
ADD conf/zz-docker.conf /usr/local/etc/php-fpm.d/
ADD conf/nginx.conf /etc/nginx/
RUN chmod 644 /etc/logrotate.d/web
