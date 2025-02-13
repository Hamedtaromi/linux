# 1. download tomcat using bellog command: 
```
yum -y install wget java-1.8.0-openjdk.x86_64
wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.78/bin/apache-tomcat-9.0.78.tar.gz ---> /opt/tomcat/
```
# 2. download sample war file
```
wget https://tomcat.apache.org/tomcat-7.0-doc/appdev/sample/sample.war  ----> /opt/tomcat/webapp/app.war
```
###3. run tomcat app ---> /opt/tomcat/bin/startup.sh
