FROM openshift/postgresql-92-centos7

ENV POSTGIS_MAJOR 2.4
ENV POSTGIS_VERSION 2.4.0+dfsg-1.pgdg80+1

USER root

RUN rpm -ivh http://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm \
      && rpm -ivh https://download.postgresql.org/pub/repos/yum/9.6/redhat/rhel-7-x86_64/pgdg-centos96-9.6-3.noarch.rpm \
      && yum -y install postgis24_96 postgis24_96-client \
      && ls -la /opt/rh/postgresql92/root/usr/share/pgsql/extension/
      #yum -y install epel-release \
      #&& yum -y install postgis \
      #&& rpm -ivh http://yum.postgresql.org/9.5/redhat/rhel-7-x86_64/pgdg-centos95-9.5-2.noarch.rpm \
      #&& yum -y install postgresql95 postgresql95-server postgresql95-libs postgresql95-contrib postgresql95-devel \
      #&& rpm -ivh http://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
      #&& rpm -ivh https://download.postgresql.org/pub/repos/yum/9.6/redhat/rhel-7-x86_64/pgdg-centos96-9.6-3.noarch.rpm
      #&& yum -y install postgis2_95 postgis2_95-client

#RUN apt-get update \
#      && apt-get install -y --no-install-recommends \
#           postgresql-$PG_MAJOR-postgis-$POSTGIS_MAJOR=$POSTGIS_VERSION \
#           postgresql-$PG_MAJOR-postgis-$POSTGIS_MAJOR-scripts=$POSTGIS_VERSION \
#           postgis=$POSTGIS_VERSION \
#      && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /docker-entrypoint-initdb.d
COPY ./initdb-postgis.sh /docker-entrypoint-initdb.d/postgis.sh
COPY ./update-postgis.sh /usr/local/bin

USER postgres
