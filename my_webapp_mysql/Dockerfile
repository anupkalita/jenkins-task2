FROM mysql

COPY ./init.sql /docker-entrypoint-initdb.d

ENV MYSQL_ROOT_PASSWORD=kinddevil
EXPOSE 3306