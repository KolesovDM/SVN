FROM ubuntu:18.04
MAINTAINER KolesovDM <kolesovdm@tmk-group.com>
LABEL version="1.0"
RUN apt-get update && apt-get install -y \
    autoconf \
    libtool \
    gcc \
    apache2 \
    subversion \
    libapache2-mod-svn \
    libsvn-dev \
  && rm -rf /var/lib/apt/lists/* \
  && a2enmod dav dav_svn \
  && mkdir -p /var/lib/svn/ \
  && chown -R www-data:www-data /var/lib/svn \
  && chmod -R 775 /var/lib/svn
USER root
COPY conf/dav_svn.conf /etc/apache2/mods-enabled/dav_svn.conf
RUN service apache2 start
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
