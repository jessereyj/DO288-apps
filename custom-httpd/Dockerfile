FROM rhscl/httpd-24-rhel7

USER 0

LABEL Component="httpd" Name="custom-httpd" Version="1" Relesae="1.0"
LABEL io.k8s.description="Custom Httpd" io.k8s.display-name="custom-httpd" io.openshift.s2i.scripts-url="image:///usr/libexec/s2i" io.openshift.expose-services="80:http"

RUN mkdir -p /tmp/src
RUN chown -R 1001:0 /tmp/src
COPY *.html /tmp/src/
COPY *.html /var/www/html
COPY .s2i/bin/ /usr/libexec/s2i

RUN sed -i "s/Listen 80/Listen 8080/g" /etc/httpd/conf/httpd.conf

ENV APP_DIRS /tmp/src /var/www/ /run/httpd /etc/httpd/logs

RUN chown -R 1001:1001 $APP_DIRS  && chgrp -R 0 $APP_DIRS && chmod -R g=u $APP_DIRS && chmod +x /usr/libexec/s2i/assemble /usr/libexec/s2i/run /usr/libexec/s2i/usage

USER 1001 

EXPOSE 8080

CMD /usr/libexec/s2i/assemble
CMD /usr/libexec/s2i/run
