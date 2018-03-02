# How to use
In order to make this docker image working you must download 
UniTime.war and place it into the docker/tomcat8/UniTime.war folder.

Latest releases for UnitTime can be found here:
https://github.com/UniTime/unitime/releases


You must build and run docker images by yourself using the following:
```bash
docker-compose build && docker-compose up
```

## How to get UniTime.war file

In order to get the version 4.2.185 you can use the following line:

```bash
wget https://github.com/UniTime/unitime/releases/download/v4.2.185/unitime-4.2_bld185.zip
-o unitime.zip && unzip -j unitime-4.2_bld185.zip web/UniTime.war
```

## Issues
When started for the first time tomcat will be started before the MySql
finishes the initialization and therefore UniTime will not work. You 
should simply start it again using docker-compose up

This can be changes by using various workarounds in docker (or switching to
another container management :) ).
