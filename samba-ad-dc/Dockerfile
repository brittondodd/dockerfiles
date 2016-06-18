FROM phusion/baseimage:0.9.17
MAINTAINER Pit Kleyersburg <pitkley@googlemail.com>

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y \
        samba \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Add startup scripts
RUN mkdir -p /etc/my_init.d
COPY samba_setup.sh /etc/my_init.d/

# Add services
RUN mkdir /etc/service/samba
COPY samba_run.sh /etc/service/samba/run
COPY samba_finish.sh /etc/service/samba/finish

EXPOSE 88
EXPOSE 135
EXPOSE 137
EXPOSE 138
EXPOSE 139
EXPOSE 389
EXPOSE 445
EXPOSE 636
EXPOSE 1024-5000
EXPOSE 3268
EXPOSE 3269
EXPOSE 5353

VOLUME ["/var/lib/samba"]

CMD ["/sbin/my_init"]
