FROM ubuntu:18.04
ENV DEBIAN_FRONTEND noninteractive
RUN apt update
RUN ln -fs /usr/share/zoneinfo/America/New_York /etc/localtime
RUN apt-get install -y tzdata
RUN dpkg-reconfigure --frontend noninteractive tzdata
RUN apt-get install wget gnupg2 -y
RUN wget -O- http://deb.kamailio.org/kamailiodebkey.gpg | apt-key add -
COPY conf/kamailio.list /etc/apt/sources.list.d/
RUN apt update
RUN apt install kamailio kamailio-sqlite-modules -y
COPY conf/kamailio.cfg /etc/kamailio/
COPY conf/kamctlrc /etc/kamailio/
COPY conf/dispatcher.list /etc/kamailio/
RUN mkdir -p /usr/local/etc/kamailio/
RUN yes | kamdbctl create
RUN kamctl add 102 secret
ENTRYPOINT ["kamailio", "-DD", "-E"]