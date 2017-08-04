From vrviumichael/ubuntu:16.04
MAINTAINER Michael Dong <michael.dong@vrviu.com>

ENV ZK_MASTER zk://127.0.0.1:2181/mesos \
    ZK_MARATHON zk://127.0.0.1:2181/marathon \
    MARATHON_HN 127.0.0.1

RUN apt-key adv --keyserver keyserver.ubuntu.com --recv E56151BF \
    && echo "deb http://repos.mesosphere.com/ubuntu xenial main" | tee /etc/apt/sources.list.d/mesosphere.list \
    && apt-get -y update && apt-get -y install mesos \
    && apt-get clean

RUN mkdir -p /export/app \
    && cd /export/app \
    && wget http://downloads.mesosphere.com/marathon/v1.4.5/marathon-1.4.5.tgz \
    && tar xvf marathon-1.4.5.tgz \
    && rm -rvf marathon-1.4.5.tgz

COPY docker-entrypoint.sh /

RUN chmod 777 /docker-entrypoint.sh

ENTRYPOINT ["/docker-entrypoint.sh"]
