FROM tomcat:7

MAINTAINER phithon <root@leavesongs.com>

RUN sed -i 's/securerandom.source=file:\/dev\/urandom/securerandom.source=file:\/dev\/.\/urandom/g' $JAVA_HOME/lib/security/java.security