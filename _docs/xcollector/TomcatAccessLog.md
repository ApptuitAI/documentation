---
title: Tomcat configuration
category: XCollector
order: 3
---
XCollector is able to extract operational metrics like the request rate,
request latency, error rate etc from Tomcat access logs.

Update Tomcat configuration to generate access logs in XCollector friendly format

`vi /etc/tomcat/server.xml`

And update the settings for AccessLogValve

```xml
<Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs"
               prefix="localhost_access" suffix=".log"
               pattern="%h %l %u %t &quot;%r&quot; %s %b &quot;%{Referer}i&quot; &quot;%{User-Agent}i&quot; %T" renameOnRotate="true"/>
```

This changes couple of settings:

1. Tomcat Access Log file name changes dynamically with time
(Ex: `localhost_access2017-09-13.log`) by default.
XCollector currently supports watching files with fixed names.
The `renameOnRotate="true"` option instructs Tomcat to add date
to the filename only on a rotation.  
The options `prefix="localhost_access" suffix=".log"` directs Tomcat to write
the access logs to `localhost_access.log` file

2. The `pattern` option directs Tomcat to log time taken to process the request
(`%T`). This data is parsed by XCollector to generate the response latency metrics

Restart Tomcat to pick up these settings:
`sudo service tomcat restart`

Xcollector runs as user `xcollector`. Make sure the xcollector user has read
permission on the access log file.

XCollector looks for Tomcat access logs by default at the following location: `/var/log/tomcat/localhost_access.log`. If your access logs are in a
different location, update the `input.path` option in `grok_tomcat.yml` file
(`vi /etc/xcollector/grok_tomcat.yml`)

Restart the XCollector service (`sudo service xcollector restart`).
