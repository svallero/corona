FROM centos:7
MAINTAINER "Harvard University FAS Research Computing" <rchelp@fas.harvard.edu>

LABEL Description="This is a base image for corona"

RUN yum -y update && yum clean all
RUN rpm -e --nodeps systemd-container systemd-container-libs; \
    yum -d 10 -y install systemd systemd-libs systemd-devel; \
    yum -y install epel-release; \
    yum -y install python-pip; \
    yum clean all

RUN pip install supervisor

#Install OpenNebula requirements

RUN yum -y install \
        gcc \
        gcc-c++ \
        libcurl-devel \
        mariadb-devel \
        ruby-devel \
        sqlite-devel \
        make \
        && yum clean all 

# Same uid/gid as local user to mount host volumes with correct ownership
RUN groupadd --gid 1000 oneadmin
RUN useradd --uid 1000 -g oneadmin -d /var/lib/one oneadmin

# Line below because otherwise one-server does not install (reason unknown)
RUN rm -rf /var/lock

COPY one-centos7.repo /etc/yum.repos.d/

COPY supervisord/supervisord.conf /etc/supervisord.conf
