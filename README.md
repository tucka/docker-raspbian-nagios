# Docker-Nagios
Docker image for Nagios

!!!Fork of smeretech/docker-debian-nagios who forked JasonRivers/Docker-Nagios!!!

Nagios Core 4.3.4  running on Raspbian with NagiosGraph & NRPE, tested on Raspberry Pi 3

### Configurations
Nagios Configuration lives in /opt/nagios/etc
NagiosGraph configuration lives in /opt/nagiosgraph/etc

### Build

```sh
docker build -t nagios_image .
```

### Running

Run with the example configuration with the following:

```sh
docker run --name nagios -p 0.0.0.0:8080:80 nagios_image
```

alternatively you can use external Nagios configuration & log data with the following:

```sh
docker run --name nagios  \
  -v /path-to-nagios/etc/:/opt/nagios/etc/ \
  -v /path-to-nagios/var:/opt/nagios/var/ \
  -v /path-to-custom-plugins:/opt/Custom-Nagios-Plugins \
  -p 0.0.0.0:8080:80 nagios_image
```

Note: The path for the custom plugins will be /opt/Custom-Nagios-Plugins, you will need to reference this directory in your configuration scripts.

For best results your Nagios image should have access to both IPv4 & IPv6 networks 

#### Credentials

The default credentials for the web interface is `nagiosadmin` / `nagios`

#### Shell

sudo docker exec -it nagios_image bash

### Extra Plugins

* Nagios nrpe [http://exchange.nagios.org/directory/Addons/Monitoring-Agents/NRPE--2D-Nagios-Remote-Plugin-Executor/details]
* Nagiosgraph [http://exchange.nagios.org/directory/Addons/Graphing-and-Trending/nagiosgraph/details]
* JR-Nagios-Plugins -  custom plugins I've created [https://github.com/JasonRivers/nagios-plugins]
* WL-Nagios-Plugins -  custom plugins from William Leibzon [https://github.com/willixix/WL-NagiosPlugins]
* JE-Nagios-Plugins -  custom plugins from Justin Ellison [https://github.com/justintime/nagios-plugins]


