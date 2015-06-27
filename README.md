# Openshift Nginx Cartridge
[Nginx](http://nginx.org/) cartridge for [Openshift](https://www.openshift.com/).
Based on [boekkooi/openshift-cartridge-nginx](https://github.com/boekkooi/openshift-cartridge-nginx).

This cartridge allow you to create a scalable nginx application.
Combine this with the [Openshift PHP Cartridge](https://github.com/sinjab/openshift-cartridge-php) and you have a scalable application using the latest versions.

Just create your app using:
```BASH
rhc create-app myapp http://cartreflect-claytondev.rhcloud.com/github/sinjab/openshift-cartridge-nginx
```

If you want to install a specific nginx version you can add `--env OPENSHIFT_NGINX_VERSION=<version>` to the command.
For example to install nginx 1.7.12 you can use:
```BASH
rhc create-app myapp --env OPENSHIFT_NGINX_VERSION=1.7.12 http://cartreflect-claytondev.rhcloud.com/github/sinjab/openshift-cartridge-nginx
```

## Versions
Currently this cartridge has the following versions:
- 1.6.3
- 1.7.12
- 1.8.0

## Modules
Currently this cartridge has the following modules:
- [Upload Progress Module](https://www.openshift.com/)
- [Cache Purge Module](https://github.com/masterzen/nginx-upload-progress-module)

If you need another version you can compile it yourself and submit a PR to get it integrated.

### Compiling a new version
To compile a new version you will first need a openshift application.
```BASH
rhc create-app nginx http://cartreflect-claytondev.rhcloud.com/github/sinjab/openshift-cartridge-nginx
```

Now clone the repository and create a `nginx` folder. Now copy the `usr/compile` directory from [this](https://github.com/sinjab/openshift-cartridge-nginx) repository.
Now set the versions you need to compile in the `nginx/compile/versions` file. Commit and push the application repository.

SSH into you app and go to the compile folder (`cd ${OPENSHIFT_REPO_DIR}/nginx/compile`) and start compiling by running the following command:
```BASH
./all
```
Once compiling is done you can download the `nginx.tar.gz` from you application.
Extract the `nginx-{version}` from the archive and place them into the `openshift-cartridge-nginx/usr` folder.
Last but not least edit the `openshift-cartridge-nginx/manifest.yml` and add the versions.

All done just commit and push to your `openshift-cartridge-nginx` repo and use:
```BASH
http://cartreflect-claytondev.rhcloud.com/github/<user>/openshift-cartridge-nginx
```
