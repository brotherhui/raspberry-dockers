FROM resin/rpi-raspbian

MAINTAINER brotherhui <17229775@qq.com>

# Install packages
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && \
	apt-get -yq install mysql-server pwgen && \
	rm -rf /var/lib/apt/lists/*

# Remove pre-installed database
RUN rm -rf /var/lib/mysql/*

# Add MySQL configuration
ADD my.cnf /etc/mysql/conf.d/my.cnf
ADD mysqld_charset.cnf /etc/mysql/conf.d/mysqld_charset.cnf

# Add MySQL scripts
ADD run.sh /run.sh
RUN chmod 755 /*.sh

# Exposed ENV
ENV MYSQL_USER pi
ENV MYSQL_PASS raspberry

# Add VOLUMEs to allow backup of config and databases
VOLUME  ["/etc/mysql", "/var/lib/mysql"]

EXPOSE 3306
CMD ["/run.sh"]
