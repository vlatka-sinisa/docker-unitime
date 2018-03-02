# docker build -t unitime-db . 

FROM mysql:5.7
LABEL maintainer="UniTime"

# COPY woebegon-data.sql /docker-entrypoint-initdb.d
# COPY schema.sql /docker-entrypoint-initdb.d
COPY *sql /docker-entrypoint-initdb.d/

