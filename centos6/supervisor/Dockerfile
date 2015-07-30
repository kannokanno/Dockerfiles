FROM centos:centos6

ENV PATH $PATH:/usr/bin

RUN yum -y update

RUN yum -y install vim

RUN yum -y install python-setuptools
RUN easy_install pip
RUN pip install supervisor
RUN pip install meld3==1.0.0

RUN mkdir /var/log/supervisor/
RUN echo_supervisord_conf > /etc/supervisord.conf
