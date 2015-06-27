# Openshift Nginx Cartridge
[Nginx](http://nginx.org/) cartridge for [Openshift](https://www.openshift.com/).
Based on [boekkooi/openshift-cartridge-nginx](https://github.com/boekkooi/openshift-cartridge-nginx).

This cartridge allow you to create a scalable nginx application.
Combine this with the [Openshift PHP Cartridge](https://github.com/sinjab/openshift-cartridge-php) and you have a scalable application using the latest versions.

Just create your app using:
```BASH
rhc create-app myapp http://cartreflect-claytondev.rhcloud.com/github/sinjab/openshift-cartridge-nginx
```

## Versions
Currently this cartridge has the following versions:
- 1.6.3
- 1.8.0 (default)
- 1.9.2

If you want to install a specific nginx version you can add `--env OPENSHIFT_NGINX_VERSION=<version>` to the command.
For example to install nginx 1.9.2 you can use:
```BASH
rhc create-app myapp --env OPENSHIFT_NGINX_VERSION=1.9.2 http://cartreflect-claytondev.rhcloud.com/github/sinjab/openshift-cartridge-nginx
```

## Types
Currently this cartridge has the following types:
- light
- fastcgi (default)
- full

If you want to install a specific nginx type you can add `--env OPENSHIFT_NGINX_TYPE=<type>` to the command.
For example to install nginx full you can use:
```BASH
rhc create-app myapp --env OPENSHIFT_NGINX_TYPE=full http://cartreflect-claytondev.rhcloud.com/github/sinjab/openshift-cartridge-nginx
```

## Additional Modules
Currently this cartridge has the following modules:
- [Fastcgi Module](http://nginx.org/en/docs/http/ngx_http_fastcgi_module.html)
- [Upload Progress Module](https://github.com/masterzen/nginx-upload-progress-module)
- [Cache Purge Module](https://github.com/FRiCKLE/ngx_cache_purge)

|                        | nginx light | nginx fastcgi | nginx full |
|------------------------|-------------|---------------|------------|
| Fastcgi Module         | no          | yes           | yes        |
| Upload Progress Module | no          | no            | yes        |
| Cache Purge Module     | no          | no            | yes        |

If you need another variation you can compile it yourself and submit a PR to get it integrated.
