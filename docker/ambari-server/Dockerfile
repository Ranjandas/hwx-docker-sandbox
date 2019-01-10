FROM centos/systemd

ENV AMBARI_MAJOR_VERSION 2.x
ENV AMBARI_VERSION 2.7.1.0
ENV OPENJDK_VERSION 1.8.0

RUN curl -o /etc/yum.repos.d/ambari.repo -L http://public-repo-1.hortonworks.com/ambari/centos7/${AMBARI_MAJOR_VERSION}/updates/${AMBARI_VERSION}/ambari.repo

RUN yum makecache && \
    yum -y install ambari-server \
    mysql-connector-java.noarch \
    mysql \
    java-${OPENJDK_VERSION}-openjdk && \
    yum clean all && \
    rm -rf /var/cache/yum

COPY etc/systemd/system/ambari-setup.service /etc/systemd/system/ambari-setup.service
COPY etc/systemd/system/ambari-db-migrate.service /etc/systemd/system/ambari-db-migrate.service

RUN systemctl enable ambari-server ambari-setup ambari-db-migrate

EXPOSE 8080
