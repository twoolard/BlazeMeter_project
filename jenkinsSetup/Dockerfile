FROM jenkins:2.46.1-alpine

#COPY plugins.txt /usr/share/jenkins/plugins.txt
#RUN /usr/local/bin/plugins.sh /usr/share/jenkins/plugins.txt
COPY plugins.txt /usr/share/jenkins/ref/plugins
RUN /usr/local/bin/install-plugins.sh


ENV INFLUXDB_VERSION 1.2.2
RUN apk add --no-cache --virtual .build-deps wget sudo dpkg && \
	cd /var &&\
	mkdir -p -v database &&\
	cd /var/database &&\
	wget -q https://dl.influxdata.com/influxdb/releases/influxdb-${INFLUXDB_VERSION}_linux_i386.tar.gz && \
    tar xvfz influxdb-${INFLUXDB_VERSION}_linux_i386.tar.gz && \
	rm -rf /var/database/influxdb-${INFLUXDB_VERSION}-1/etc/influxdb.conf &&\
	rm -rf *.tar.gz
    
COPY influxdb.conf /var/database/influxdb-${INFLUXDB_VERSION}-1/usr/bin


#EXPOSE 8086
#EXPOSE 8083
#EXPOSE 2003
#VOLUME /var/lib/influxdb

#CMD influxd -config /var/jenkins_home/influxdb.conf
#CMD influxd