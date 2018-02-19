# docker build -t unitime-db . && docker run -it --rm -e MYSQL_RANDOM_ROOT_PASSWORD=yes  unitime-db
## docker run -it --rm  -p unitime-db
## docker run -it --rm unitime-web

FROM mysql:5.7
LABEL maintainer="UniTime"

RUN apt-get update && apt-get install -y wget unzip 
# RUN wget https://github.com/UniTime/unitime/releases/download/v4.1.175/unitime-4.1_bld175.zip

COPY woebegon-data.sql /docker-entrypoint-initdb.d
COPY schema.sql /docker-entrypoint-initdb.d
# RUN unzip /tmp/unitime.zip -d /tmp/unitime

RUN sed -i "s|#bind-address     = 127.0.0.1|#bind-address     = 0.0.0.0|g" /etc/mysql/mysql.conf.d/mysqld.cnf


# COPY ../UniTime/unitime.zip
#RUN cp /tmp/unitime/doc/mysql/schema.sql  /docker-entrypoint-initdb.d
#RUN cp /tmp/unitime/doc/mysql/woebegon-data.sql  /docker-entrypoint-initdb.d
# RUN mysql -uroot  -f < /tmp/unitime/doc/mysql/schema.sql
# RUN mysql -utimetable -punitime < /tmp/unitime/doc/mysql/woebegon-data.sql


