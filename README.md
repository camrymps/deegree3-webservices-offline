# Deegree3 Webservices Offline

"Offline" version of [deegree3-docker](https://hub.docker.com/r/deegree/deegree3-docker/). Includes WAR file and all XSD files.

[![Docker Image CI](https://github.com/deegree/deegree3-docker/actions/workflows/docker-image.yaml/badge.svg)](https://github.com/deegree/deegree3-docker/actions/workflows/docker-image.yaml)

# Supported tags and respective `Dockerfile` links

- deegree 3.5.x (JDK 11/Tomcat 9): `3.5.7`, `3.5`, `latest` - [Dockerfile](https://github.com/camrymps/deegree3-webservices-offline/blob/master/3.5/Dockerfile)
# Quick reference

## deegree web services on Docker
Official Dockerfile for [deegree web services](https://www.deegree.org/). This repository contains a ```Dockerfile``` for building Docker images containing ready-to-use deegree webservices.
 
Please consult the [deegree documentation](https://download.deegree.org/documentation/current/html/) for further information how to 
configure and use deegree webservices. The [Docker web site](https://www.docker.com/) provides all information 
about Docker.

## Docker images on Docker hub

[![deegree3-webservices-offline](http://dockeri.co/image/deegree/deegree3-webservices-offline)](https://hub.docker.com/r/deegree/deegree3-webservices-offline/)

https://hub.docker.com/r/deegree/deegree3-webservices-offline/

## How to use it

Use the following command to pull the latest image:

```
docker pull deegree/deegree3-webservices-offline:latest
```

To start a docker container with the name `deegree` on port 8080 run the following command:

```
docker run -d --name deegree -p 8080:8080 deegree/deegree3-webservices-offline:latest
```
Running the image with `-d` runs the container in detached mode, leaving the container running in the background.
The `--name` flag is setting the name for the container. The `-p` flag redirects a public port to a private port inside the container.

### How to access deegree administration console

To access the deegree webservices console start a browser of your choice and open the URL:

http://<container_ip>:8080/deegree-webservices/, the `<container_ip>` depends on the docker networking mode.
http://localhost:8080/deegree-webservices/ should work with bridge mode.

XSDs are hosted at [http://localhost:8080/deegree-webservices-xsd/](http://localhost:8080/deegree-webservices-xsd/).

Continue with configuration of deegree as described in the [getting started guide](https://download.deegree.org/documentation/current/html/#anchor-lightly) of the deegree webservices handbook.

### How to access deegree command-line interface (CLI)

After you have started the container you can run the deegree CLI tools with:

```
docker exec -w /opt deegree java -jar deegree-tools-gml.jar -help
```

Now you can use the deegree CLI to generate configuration files based on an GML application schema using the following command:

```
docker exec -w /opt/ deegree java -jar deegree-tools-gml.jar SqlFeatureStoreConfigCreator -format=all -dialect=postgis -cycledepth=1 -schemaUrl=https://inspire.ec.europa.eu/schemas/ps/4.0/ProtectedSites.xsd
```

Read further in the [deegree webservices handbook](https://download.deegree.org/documentation/current/html/#deegree-gml-tools) how to use the deegree command-line interface.
