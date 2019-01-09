FROM centos/systemd

ENV AMBARI_MAJOR_VERSION 2.x
ENV AMBARI_VERSION 2.7.1.0
ENV OPENJDK_VERSION 1.8.0
ENV HDP_MAJOR_VERSION 3.x
ENV HDP_VERSION 3.0.1.0

RUN curl -o /etc/yum.repos.d/ambari.repo -L http://public-repo-1.hortonworks.com/ambari/centos7/${AMBARI_MAJOR_VERSION}/updates/${AMBARI_VERSION}/ambari.repo

RUN curl -o /etc/yum.repos.d/ambari-hdp-1.repo -L http://public-repo-1.hortonworks.com/HDP/centos7/${HDP_MAJOR_VERSION}/updates/${HDP_VERSION}/hdp.repo

RUN yum makecache &&\
    yum -y install ambari-agent \
    java-${OPENJDK_VERSION}-openjdk \
    chrony \
    initscripts \
    which \
    unzip \
    zookeeper-server \
    hadoop \
    hbase \
    hadoop-yarn \
    hadoop-mapreduce \
    hadoop-client \
    hadoop-libhdfs \
    smartsense-hst \
    ambari-metrics-collector \
    ambari-metrics-monitor \
    snappy \
    snappy-devel \
    ambari-metrics-hadoop-sink \
    ambari-metrics-grafana-sink \
    ambari-metrics-grafana \
    python-kerberos \
    kafka \
    knox \
    storm \
    yum clean all && \
    rm -rf /var/cache/yum

COPY etc/systemd/system/ambari-agent-setup.service /etc/systemd/system/ambari-agent-setup.service

RUN systemctl enable ambari-agent ambari-agent-setup
