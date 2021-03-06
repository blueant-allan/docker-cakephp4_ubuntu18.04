## Dockerfile development configuration for CakePHP version 4.x using Ubuntu 18.04 as base image

Stack

* Nginx
* PHP 7.4
* CakePHP vesion 4.x
* PPA ondrej/php

Loaded PHP Extensions

* Mysql
* Intl
* Mbstring
* Zip
* Xml
* Sqlite3


## Compile the docker file

```
docker build -t cakephp4-image -f Dockerfile.dev .
```

## Create instance of the container

```
docker run -p 8080:80 -it --name conainer_name-web --mount type=bind,source="$(pwd)",target=/var/www/html cakephp4-image
```


## Manage the container

```
docker exec -it conainer_name-web bash
```


## Usage

1. You can start by create a CakePHP project via composer

```
composer create-project --prefer-dist cakephp/app <project_name>
```

2. Build the dockerfile configuration and create a container for it.

3. Now that you have your container setup, let us setup CakePHP

```
docker exec -it <project-name> bash
	
# let us complete the CakePHP installation
php composer.phar install
```

This document assumes that you have composer.phar file.

4. You should be able to load your web-application from your browser with the port you incidated above. Example: http://localhost:8080

5. Update your app-config file so that you can connect to your database
