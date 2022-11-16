FROM alpine

ENV MYSQL_USER = "zabbix"
ENV MYSQL_DATABASE = "zabbix"
ENV MYSQL_PASSWORD = "123Mudar"

ADD schema.sql /usr/share/zabbix-sql-scripts/mysql/server.sql.gz
RUN apt update -y \
    apt install mysql -y\
    mysql -uroot -p123Mudar -e "CREATE DATABASE ${MYSQL_DATABASE} /*\!40100 DEFAULT CHARACTER SET utf8 */;" \
    mysql -uroot -p123Mudar -e "CREATE USER ${MYSQL_USER}@% IDENTIFIED BY '${MYSQL_PASSWORD}';" \
    mysql -uroot -p123Mudar -e "GRANT ALL PRIVILEGES ON ${MAINDB}.* TO '${MYSQL_USER}'@'localhost';" \
    mysql -uroot -p123Mudar -e "FLUSH PRIVILEGES;" \
    cat /usr/share/zabbix-sql-scripts/mysql/server.sql | mysql --default-character-set=utf8mb4 -uzabbix -p zabbix 

VOLUME mysql/data/ : /var/lib/mysql/data/

EXPOSE 3306
