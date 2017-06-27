FROM resin/rpi-raspbian:jessie

MAINTAINER brotherhui <17229775@qq.com>

RUN echo "deb http://ftp.debian.org/debian jessie-backports main" >> /etc/apt/sources.list.d/jessie-backports.list

RUN apt-get update && apt-get -t jessie-backports install -y nginx

# forward request and error logs to docker log collector
RUN ln -sf /dev/stdout /var/log/nginx/access.log
RUN ln -sf /dev/stderr /var/log/nginx/error.log

# set timezone
ENV TZ=Asia/Shanghai
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

#use the disk space
VOLUME ["/usr/share/nginx/www"]
VOLUME ["/etc/nginx"]

#default 80 port htmls directory
VOLUME ["/var/www/html"]

#upload sever configs for different domains
VOLUME ["/etc/nginx/sites-available"]
VOLUME ["/etc/nginx/conf.d"]

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]