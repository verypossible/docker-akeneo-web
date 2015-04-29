# docker-akeneo-web
An nginx front end for the
[akeneo](https://registry.hub.docker.com/u/spartan/akeneo/) docker image.

## EXPOSE
This exposes port 80.

## ENV

### APP_ENVIRONMENT

The APP_ENVIRONMENT. By default this is set to production. If you set this to
development then it will update the front controller to point at app_dev.php
rather than app.php.

### WEB_PHP_HOST

This should be the name of the php akeneo docker container that you link into
this container. That way nginx will know where to pass the php fpm requests.
The default value is: `php`

### WEB_SERVER_NAME

The server_name for the nginx configuration.

### WEB_ERROR_LOG_LEVEL

The nginx error log level.

### WEB_STATUS_ALLOWED_IP

An ip that is allowed to view the php-fpm and nginx status pages.

If you set this variable to `HOST_IP` then it'll get replaced by the docker
host's ip in the entrypoint.

## ENTRYPOINT

The entrypoint will set up the front controller environment file off of the
value of the APP_ENVIRONMENT variable. It will then generate a nginx config for
akeneo off of the values of the ENVIRNOMENT variables.

## CMD

The default command is to run nginx in the foreground.
