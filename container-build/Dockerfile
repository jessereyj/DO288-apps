# Use the httpd-parent image as base
FROM quay.io/redhattraining/httpd-parent

EXPOSE 8080

LABEL io.k8s.description="Apache Httpd" \
      io.k8s.display-name="Apache HTTP Server" \
      io.openshift.expose-services="8080:http" \
      io.openshif.tags="apache, httpd"

RUN sed -i "s/Listen 80/Listen 8080/g" /etc/httpd/conf/httpd.conf

ENV APP_DIRS="/var/log/httpd /var/run/httpd"

RUN chgrp -R 0 $APP_DIRS && chmod -R g=u $APP_DIRS

USER 1001


