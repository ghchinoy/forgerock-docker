# ForgeRock OpenDJ

This repository contains Dockerfile and resources to build a Docker image with ForgeRock version OpenDJ-2.7.0-20150306 (nightly, as of this commit) with Example.ldif containing users.

## Usage

### from Docker Hub

If you don't want to check out this repo, you can use the latest build of the image on Docker Hub: [ghchinoy/forgerock](https://registry.hub.docker.com/u/ghchinoy/forgerock/)

The following commands will run container named `opendj`

    docker pull ghchinoy/forgerock
    docker run -d -p 1389:1389 -p 1636:1636 -p 4444:4444 --name opendj ghchinoy/forgerock


### Build and Run from Dockerfile

Check out this repo and issue the following commands to build then run a Docker container named `opendj`

	docker build -t local/forgerock -f Dockerfile.opendj .
	docker run -d -p 1389:1389 -p 1636:1636 -p 4444:4444 --name opendj local/forgerock

Access at ldap://_dockerip_:1389

For boot2docker users, ldap://_boot2dockerip_:1389

Note the `opendj-install.properties`
* sets root user DN and password
* installs Example.ldif so there's data



## To Do

* `startOpenDJ` script is intended to also start the REST access to OpenDJ, but currently doesn't work