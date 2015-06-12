This docker images is extended from https://registry.hub.docker.com/u/tutum/influxdb/

tutum-docker-influxdb
=====================
InfluxDB image



Usage
-----

To create the image `influxdbcollectd`, execute the following command on tutum-docker-influxdb folder:

    docker build -t influxdbcollectd .


Running your InfluxDB image with collectd and udp plugin enabled
--------------------------

Expose influxDB admin UI and rest endpoint on port `8083` and `8086` in all interfaces to your container. Expose udp port 4444 for collecting the data using UDP client and udp port 25827 for collectd. Create influxdb data directory on docker host '/opt/influxdb' and give write permission for docker user and attach it as docker volume.

    docker run -d --name influxdb -p 8086:8086 -p 8083:8083 -p 4444:4444/udp -p 25827:25827/udp -v /opt/influxdb:/data  -e UDP_DB="logdb" -e PRE_CREATE_DB="logdb" influxdbcollectd


Configuring collectd database for InfluxDB
-------------------------
Open your browse to access `localhost:8083` to configure InfluxDB. Fill the port which maps to `8086`. The default credential is `root:root`. Please change it as soon as possible. Create "collectd" database in  influxdb from admin ui.

