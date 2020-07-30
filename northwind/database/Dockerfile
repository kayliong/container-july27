FROM mysql:5.7

ENV MYSQL_ROOT_PASSWORD=changeit MYSQL_PORT=3306 MYSQL_DB_PATH=/var/lib/mysql

ADD 0-northwind-default-current-timestamp.sql /docker-entrypoint-initdb.d
ADD 1-northwind-data.sql /docker-entrypoint-initdb.d

#health check
HEALTHCHECK --interval=30s --timeout=3s --start-period=4s --retries=3 \
    CMD mysqladmin ping -uroot -p${MYSQL_ROOT_PASSWORD} || exit 1

# post
EXPOSE ${MYSQL_PORT}

# volume
VOLUME ${MYSQL_DB_PATH}

