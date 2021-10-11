FROM openjdk:8-jre

LABEL MAINTAINER="Kushal Mehta <kushal.mt@gmail.com>"
EXPOSE 8080

COPY build/docker/context-start /opt/context-start
# install needed system modules
RUN apt-get update \
    && apt-get install -y --allow-unauthenticated bash \
                                                  curl \
                                                  jq \
    && rm -rf /var/lib/apt/lists/* \
    && mkdir -p /etc/test-tool/ \
    && mkdir -p /mnt/files \
    && mkdir -p /opt/data

COPY target/test-*.jar /opt/.
COPY target/classes/application.properties /etc/test-tool/.
COPY build/docker/context-start /opt/context-start
RUN chmod a+x /opt/context-start 

CMD /opt/context-start
