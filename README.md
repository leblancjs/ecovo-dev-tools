# Dev Tools - C'est pas moi qui l'dit!
## Introduction 
C'est pas moi qui l'dit!

It's not easy when you want to run all these little micro-services locally. To make things easier, use `dev-tools`. Nothing fancy. Just a `docker-compose` configuration and some other stuff to run it all.

## Prerequisites
In order for any of this to work, you need to have `Docker` installed, have it running, and be logged in to `Docker Hub` using the Ecovo account credentials which can be found on `Google Drive`.

## Run
### Everything
Enter the following command in your terminal:

```
docker-compose up
```

To stop it all, just use `Ctrl-C`.

### Only What You Need
To run only a few services, enter the following command in your terminal:

```
docker-compose up -d <A-SERVICE> <ANOTHER-SERVICE> ...
```

To stop it all, you'll need to enter the following command in your terminal:

```
docker-compose stop
```

#### Available Services
The available services are in the `docker-compose.yml` file, but since you're here, you're probably lazy. So here they are:
* gateway-service
* user-service
* trip-service
* trip-search-service

#### A Note On Environment Variables
In a situation where you want to debug a service, you will need to change the environment files.

For example, if you want to run all the services, but the `user-service` since you want to run it using the debugger in VS Code, you'll need to update the `gateway-service.env` file.

You'll need to change

```
USER_SERVICE_HOST=http://user-service:8080
```

to

```
USER_SERVICE_HOST=http://host.docker.internal/<PORT>
```

where `PORT` is the port on which the service is being run.