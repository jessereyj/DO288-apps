FROM rhscl/httpd-24-rhel7

#MAINTAINER "Jesserey Joseph" "jesserey.joseph@ibm.com"

#LABEL Component="httpd" Name="custom-httpd" Version="1" Relesae="1.0"
#LABEL io.k8s.description="Custom Httpd" io.k8s.display-name="custom-httpd" io.openshift.s2i.scripts-url="image:///usr/libexec/s2i" io.openshift.expose-services="8080:http"

LABEL io.k8s.display-name="httpd-24-rhel7" io.openshift.s2i.build.image="httpd-24-rhel7"

USER 0
#RUN mkdir -p /var/www/html
ADD index.html /tmp/src/
RUN chown -R 1001:0 /tmp/src
#COPY .s2i/bin/ /usr/libexec/s2i

#ENV APP_DIRS /tmp/src/ /var/www/ 
#RUN chown -R 1001:1001 $APP_DIRS  && chgrp -R 0 $APP_DIRS && chmod -R g=u $APP_DIRS && chmod +x /usr/libexec/s2i/assemble /usr/libexec/s2i/run /usr/libexec/s2i/usage


USER 1001 
#EXPOSE 8080

RUN /usr/libexec/s2i/assemble
CMD /usr/libexec/s2i/run
