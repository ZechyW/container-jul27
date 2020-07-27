FROM mysql:5.7

ENV MYSQL_ROOT_PASSWORD=rootroot MYSQL_PORT=3306 MYSQL_DB=/var/lib/mysql

ADD 0-northwind-default-current-timestamp.sql /docker-entrypoint-initdb.d
ADD 1-northwind-data.sql /docker-entrypoint-initdb.d

EXPOSE ${MYSQL_PORT}

VOLUME ${MYSQL_DB}

HEALTHCHECK --interval=30s --timeout=5s --start-period=10s --retries=3 CMD mysqladmin ping -uroot -p${MYSQL_ROOT_PASSWORD} || exit 1