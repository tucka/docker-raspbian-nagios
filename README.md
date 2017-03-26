# Docker-Nagios
Docker image for Nagios

!!!Fork of JasonRivers/Docker-Nagios!!!

Nagios Core 4.3.1 running on Debian with NagiosGraph & NRPE

### Configurations
Nagios Configuration lives in /opt/nagios/etc
NagiosGraph configuration lives in /opt/nagiosgraph/etc

### Install

```sh
docker pull smeretech/docker-debian-nagios:4.3.1
```

### Running

Run with the example configuration with the following:

```sh
docker run --name nagios -p 0.0.0.0:8080:80 smeretech/docker-debian-nagios:4.3.1
```

alternatively you can use external Nagios configuration & log data with the following:

```sh
docker run --name nagios  \
  -v /path-to-nagios/etc/:/opt/nagios/etc/ \
  -v /path-to-nagios/var:/opt/nagios/var/ \
  -v /path-to-custom-plugins:/opt/Custom-Nagios-Plugins \
  -p 0.0.0.0:8080:80 smeretech/docker-debian-nagios:4.3.1
```

Note: The path for the custom plugins will be /opt/Custom-Nagios-Plugins, you will need to reference this directory in your configuration scripts.

For best results your Nagios image should have access to both IPv4 & IPv6 networks 

#### Credentials

The default credentials for the web interface is `nagiosadmin` / `nagios`

#### Shell

sudo docker exec -it nagios bash

### Extra Plugins

* Nagios nrpe [http://exchange.nagios.org/directory/Addons/Monitoring-Agents/NRPE--2D-Nagios-Remote-Plugin-Executor/details]
* Nagiosgraph [http://exchange.nagios.org/directory/Addons/Graphing-and-Trending/nagiosgraph/details]
* JR-Nagios-Plugins -  custom plugins I've created [https://github.com/JasonRivers/nagios-plugins]
* WL-Nagios-Plugins -  custom plugins from William Leibzon [https://github.com/willixix/WL-NagiosPlugins]
* JE-Nagios-Plugins -  custom plugins from Justin Ellison [https://github.com/justintime/nagios-plugins]


