---
title: Nginx configuration
category: XCollector
order: 2
---
NGINX Access log related configuration is in the file: `vi /etc/xcollector/grok_nginx.yml`

XCollector looks for NGINX access logs by default at the following location: `/var/log/nginx/access.log`. If your access logs are in a different location, update the `input.path` option to the right location

Xcollector runs as user `xcollector`. Make sure the xcollector user has read
permission on the access log file.

Check if your current log format is supported out of the box. Nginx configuration file `/etc/nginx/nginx.conf` should have one of:  
 1. an entry `access_log logs/access.log combined;` (combined is a predefined log format in nginx)
 1. OR you are using the default values for `http:log_format` and `http:access_log` options, which look like this:
 ```
     http {
       log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                         '$status $body_bytes_sent "$http_referer" '
                         '"$http_user_agent" "$http_x_forwarded_for"';

       access_log  /var/log/nginx/access.log  main;
```

##### If your access log is supported out of the box:
No more changes are necessary to the configuration. However, the default configuration does not have enough data to extract metrics like response times, upstream latency etc. To get richer metrics, it is ***highly recommended*** that you log additional fields like `$request_length $bytes_sent $request_time $upstream_response_time` in the access log.

To add these fields to the log file, update `http:log_format` and `http:access_log` options in `/etc/nginx/nginx.conf` to:
```
http {
#    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
#                      '$status $body_bytes_sent "$http_referer" '
#                      '"$http_user_agent" "$http_x_forwarded_for"';
#
#    access_log  /var/log/nginx/access.log  main;

     log_format apptuit '$remote_addr - $remote_user [$time_local] "$request" '
                        '$status $body_bytes_sent "$http_referer" '
                        '"$http_user_agent" "$http_x_forwarded_for"'
                        ' $request_length $bytes_sent $request_time $upstream_response_time';

    access_log  /var/log/nginx/access.log  apptuit;
```

###### If your current access log format is NOT supported out of the box:
 1. Verify that the following fields are enabled in the log:  
   `$request $status $request_length $bytes_sent $request_time $upstream_response_time`
 1. Create a pattern that matches your log file format as described in [CustomGrokPatterns](CustomGrokPatterns)
 1. Update the correct patterns in `/etc/xcollector/grok_nginx.yml` file under the section `grok: additional_patterns:`.
