FROM centos:centos6

RUN yum -y update && yum -y install \
    httpd \
    php \
    php-mysql \
    && yum clean all \
    && sed -i 's/\#ServerName www\.example\.com\:80/ServerName localhost/g' /etc/httpd/conf/httpd.conf
EXPOSE 80
CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]
