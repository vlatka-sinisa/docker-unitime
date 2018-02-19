# How to use
In order to make this docker image working you must download 
UniTime.war and place it into the docker/tomcat8/UniTime.war folder.


## Issues
When started for the first time tomcat will be started before the MySql
finishes the initialization and therefore UniTime will not work. You 
should simply start it again using docker-compose up

This can be changes by using various workarounds in docker (or switching to
another container management :) ).
