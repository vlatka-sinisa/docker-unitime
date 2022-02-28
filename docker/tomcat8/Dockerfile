# docker build -t unitime-web . && docker run -it --rm  -p 8888:8080 unitime-web
## docker run -it --rm unitime-web

FROM tomcat:8.0.50-jre8-slim
LABEL maintainer="UniTime"

RUN apt-get update && \
	apt-get install -y wget unzip && \
	wget https://repo1.maven.org/maven2/mysql/mysql-connector-java/5.1.38/mysql-connector-java-5.1.38.jar && \
	echo 'JAVA_OPTS=”-Djava.awt.headless=true -Xmx2g -XX:+UseConcMarkSweepGC”' >> /etc/default/tomcat8 && \
	cp mysql-connector-java-5.1.38.jar /usr/local/tomcat/lib && \
	mkdir /usr/local/tomcat/data && \
	sed -i "s|-Djava.protocol.handler.pkgs=org.apache.catalina.webresources|-Djava.protocol.handler.pkgs=org.apache.catalina.webresources -Djava.awt.headless=true -Xmx2g -XX:+UseConcMarkSweepGC|g" /usr/local/tomcat/bin/catalina.sh && \
	echo 'tmtbl.custom.properties=/usr/local/tomcat/conf/unitime.properties' >> /usr/local/tomcat/conf/catalina.properties && \
	chmod 777 /usr/local/tomcat/data
	
COPY UniTime.war /usr/local/tomcat/webapps
COPY unitime.properties /usr/local/tomcat/conf/unitime.properties
