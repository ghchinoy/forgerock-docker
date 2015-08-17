# ForgeRock OpenDJ

This repository contains Dockerfile and resources to build a Docker image with ForgeRock version OpenDJ 2.7.0-20150429 ([nightly](https://forgerock.org/downloads/opendj-builds/), as of this commit) with [Example.ldif](opendj.forgerock.org/Example.ldif) containing users.
Please see `opendj-install.properties` for default cn and password (see below, Build Notes, for other info).

## Usage

### Run from Docker Hub

If you don't want to check out this repo, you can use the latest build of the image on Docker Hub: [ghchinoy/forgerock](https://registry.hub.docker.com/u/ghchinoy/forgerock/)

The following commands will run container named `opendj`

    docker pull ghchinoy/forgerock
    docker run -d -p 1389:1389 -p 1636:1636 -p 4444:4444 --name opendj ghchinoy/forgerock


### Build and Run from Dockerfile

Check out this repo and issue the following commands to build then run a Docker container named `opendj`

#### Check out

    git clone https://github.com/ghchinoy/forgerock-docker.git
    cd forgerock-docker

#### Build

	docker build -t local/forgerock -f Dockerfile.opendj .

#### Run

	docker run -d -p 1389:1389 -p 1636:1636 -p 4444:4444 --name opendj local/forgerock

Access at ldap://_dockerip_:1389

For [boot2docker](https://docs.docker.com/installation/mac/) users, ldap://_boot2dockerip_:1389


### Build Notes

 `opendj-install.properties`
* sets root user DN, password, ports
* installs Example.ldif so there's data; one can comment out `ldifFile` property to build an empty LDAP



## To Do

* `startOpenDJ` script is intended to also start the [REST access to OpenDJ](http://docs.forgerock.org/en/opendj/2.6.0/admin-guide/index.html#setup-rest2ldap-connection-handler), but currently doesn't work
* Change example.ldif to be mountable, so that users can specify their own ldif
* Add a script to download the latest OpenDJ
