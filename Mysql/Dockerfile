FROM ubuntu

ENV MYSQL_USER=zabbix
ENV MYSQL_DATABASE=zabbix
ENV MYSQL_PASSWORD=123Mudar
ENV MYSQL_ROOT_PASSWORD=Web318798

ADD schema.sql /usr/share/zabbix-sql-scripts/mysql/server.sql.gz

RUN apt update -y && apt install mysql-server-8.0 -y && \
service mysql start && \
mysql -uroot -pWeb318798 -e "CREATE DATABASE ${MYSQL_DATABASE} /*\!40100 DEFAULT CHARACTER SET utf8 */;" && \
mysql -uroot -pWeb318798 -e "CREATE USER ${MYSQL_USER}@localhost IDENTIFIED BY '${MYSQL_PASSWORD}';" && \
mysql -uroot -pWeb318798 -e "GRANT ALL PRIVILEGES ON ${MYSQL_DATABASE}.* TO '${MYSQL_USER}'@'localhost';" && \
mysql -uroot -pWeb318798 -e "FLUSH PRIVILEGES;" && \
cat /usr/share/zabbix-sql-scripts/mysql/server.sql | mysql --default-character-set=utf8mb4 -uzabbix -p123Mudar zabbix

# VOLUME ./var/lib/mysql/:/var/lib/mysql/

EXPOSE 3306
