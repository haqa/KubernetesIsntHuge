FROM    alpine:edge

VOLUME  "/etc/nagios" "/var/nagios"

EXPOSE  80

RUN     apk --no-cache add bash nagios nagios-plugins-all nagios-web apache2 php7-apache2 php7 php7-apcu rsyslog runit && \
        cp -av /etc/nagios /etc/nagios.skel && \
        cp -av /var/nagios /var/nagios.skel && \
        rm -rf /etc/nagios/* /var/nagios/* /etc/apache2/conf.d /etc/lighttpd /var/www/localhost/htdocs && \
        chown nagios:nagios /etc/nagios /var/nagios && \
        ln -s /usr/share/nagios/htdocs /var/www/localhost/htdocs

ADD     startup /usr/local/bin/
COPY    etc /etc
COPY    htdocs/* /usr/share/nagios/htdocs
CMD     /usr/local/bin/startup
