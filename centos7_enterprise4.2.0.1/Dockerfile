FROM centos:latest
RUN yum -y update && yum -y install cyrus-sasl cyrus-sasl-gssapi cyrus-sasl-plain krb5-libs libcurl libpcap lm_sensors-libs net-snmp net-snmp-agent-libs openldap openssl rpm-libs tcp_wrappers-libs && yum -y install https://repo.mongodb.com/yum/redhat/7/mongodb-enterprise/4.2/x86_64/RPMS/mongodb-enterprise-4.2.0-1.el7.x86_64.rpm https://repo.mongodb.com/yum/redhat/7/mongodb-enterprise/4.2/x86_64/RPMS/mongodb-enterprise-mongos-4.2.0-1.el7.x86_64.rpm https://repo.mongodb.com/yum/redhat/7/mongodb-enterprise/4.2/x86_64/RPMS/mongodb-enterprise-server-4.2.0-1.el7.x86_64.rpm https://repo.mongodb.com/yum/redhat/7/mongodb-enterprise/4.2/x86_64/RPMS/mongodb-enterprise-shell-4.2.0-1.el7.x86_64.rpm https://repo.mongodb.com/yum/redhat/7/mongodb-enterprise/4.2/x86_64/RPMS/mongodb-enterprise-tools-4.2.0-1.el7.x86_64.rpm && yum clean all
RUN groupadd mongodb && useradd -d /home/mongodb -ms /bin/bash -g mongodb -G mongodb -p mongodb mongodb
RUN mkdir -p /data/db /data/configdb \
  && chown -R mongodb:mongodb /data/db /data/configdb
VOLUME /data/db /data/configdb
#COPY docker-entrypoint.sh /usr/local/bin/
#ENTRYPOINT ["docker-entrypoint.sh"]
EXPOSE 27017
USER mongodb
CMD ["mongod","--bind_ip_all"]
