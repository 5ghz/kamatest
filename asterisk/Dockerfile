FROM ubuntu:18.04
ENV DEBIAN_FRONTEND noninteractive
RUN apt update
RUN ln -fs /usr/share/zoneinfo/America/New_York /etc/localtime
RUN apt-get install -y tzdata
RUN dpkg-reconfigure --frontend noninteractive tzdata
RUN apt-get install wget gnupg2 -y
RUN apt-get install asterisk -y

RUN echo '[siptrunk-kamailio] \n\
host=172.20.128.2 \n\
port=5060 \n\
type=friend \n\
disallow=all \n\
allow=alaw \n\
allow=opus \n\
context=public \n\
qualify=yes'  >> /etc/asterisk/sip.conf

ENTRYPOINT [ "/usr/sbin/asterisk", "-f" ]
