# docker build -t unitime-web . && docker run -it --rm  -p 8888:8080 unitime-web
## docker run -it --rm unitime-web

FROM tomcat:8.0.50-jre8-slim
LABEL maintainer="UniTime"

RUN echo 'JAVA_OPTS=”-Djava.awt.headless=true -Xmx2g -XX:+UseConcMarkSweepGC”' >> /etc/default/tomcat8
RUN apt-get update && apt-get install -y wget unzip && wget  http://central.maven.org/maven2/mysql/mysql-connector-java/5.1.38/mysql-connector-java-5.1.38.jar
# RUN wget https://github.com/UniTime/unitime/releases/download/v4.1.175/unitime-4.1_bld175.zip
# RUN unzip unitime-4.1_bld175.zip -d unitime

RUN cp mysql-connector-java-5.1.38.jar /usr/local/tomcat/lib
RUN mkdir /usr/local/tomcat/data
#RUN chown tomcat8 /var/lib/tomcat8/data
RUN chmod 777 /usr/local/tomcat/data

COPY UniTime.war /usr/local/tomcat/webapps

RUN sed -i "s|-Djava.protocol.handler.pkgs=org.apache.catalina.webresources|-Djava.protocol.handler.pkgs=org.apache.catalina.webresources -Djava.awt.headless=true -Xmx2g -XX:+UseConcMarkSweepGC|g" /usr/local/tomcat/bin/catalina.sh
RUN echo 'tmtbl.custom.properties=/usr/local/tomcat/conf/unitime.properties' >> /usr/local/tomcat/conf/catalina.properties

COPY unitime.properties /usr/local/tomcat/conf/unitime.properties
