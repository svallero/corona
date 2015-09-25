FROM dockernebula/base:latest
MAINTAINER "Harvard University FAS Research Computing" <rchelp@fas.harvard.edu>

LABEL Description="This is a OpenNebula head node image for DockerNebula" Version="0.2"

RUN yum -y update && yum clean all
RUN yum -y install \
    opennebula-server \
    opennebula-flow \
    opennebula-sunstone \
    && yum clean all

RUN gem install --no-ri --no-rdoc aws-sdk --version "= 1.33"
RUN gem install --no-ri --no-rdoc \
    rack \
    sinatra \
    thin \
    zendesk_api \
    sqlite3 \
    sequel \
    amazon-ec2 \
    uuidtools \
    curb \
    net-ldap \
    builder \
    trollop \
    treetop \
    parse-cron \
    ox mysql \
    softlayer_api \
    configparser azure