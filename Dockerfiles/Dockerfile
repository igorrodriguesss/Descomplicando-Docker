FROM debian

RUN apt-get update && apt-get install -y apache2 curl 
ENV APACHE_LOCK_DIR="/var/lock"
ENV APACHE_PID_FILE="/var/run/apache2/apache2.pid"
ENV APACHE_RUN_USER="www-data"
ENV APACHE_RUN_DIR="/var/run/apache2"
ENV APACHE_RUN_GROUP="www-data"
ENV APACHE_LOG_DIR="/var/log/apache2"

ADD index.html /var/www/html/ 

HEALTHCHECK --interval=1m --timeout=5s \ 
    CMD curl -f http://localhost/ || exit 1

LABEL description="Webserver"
LABEL version="1.0.0"

USER root

WORKDIR /var/www/html/

VOLUME /var/www/html/
EXPOSE 80

ENTRYPOINT ["/usr/sbin/apachectl"]
CMD ["-D", "FOREGROUND"]