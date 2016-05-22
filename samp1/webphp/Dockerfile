FROM centos:centos6

RUN yum -y update && yum -y install \
    httpd \
    php \
    php-mysql \
    && yum clean all
COPY public-html /var/www/html/
EXPOSE 80
CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
