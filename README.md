# Nginx reverse proxy Helper
NGINX reverse proxy server

Used to be the frontend when deploying Docker containers on platforms
Default image is from Linuxserver: https://docs.linuxserver.io/images/docker-nginx

At this moment, a limited set of config options are available. They will be added later.

## Reverse proxy config

For every container (or other service/server) you can add a proxy config with the variable list `nginx__proxy_confs_subdomain`. If you forward to containers, connect the to the same docker network for easy name resolution and security.

This example will forward incoming requests for `dash.example.com` on port 80 to the container named `dashboard` on port 9090, port 80 (http)
```
nginx__proxy_confs_subdomain:
 - server_name: dash.example.com
   listen: 80
   enable_ldap: false
   enable_authelia: false
   default_upstream_proto: http
   default_upstream_url: dashboard
   default_upstream_port: 9090
```

## Site files
If you wnat to copy a website directory, place them in `/files/nginx/sites/<site_directory>`

## Site-conf files
If you want specific site-config files to be copied, place them in you're playbook dir `/files/nginx/site-confs/` they must be in nginx site config file <site.conf>
