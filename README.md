# ForgeRock OpenDJ

Builds a Docker image with ForgeRock version OpenDJ-2.7.0-20150306 (nightly, as of this commit).

Note the `opendj-install.properties`
* sets root user DN and password
* installs Example.ldif so there's data


## Installation

	docker build -t local/forgerock -f Dockerfile.opendj .
	docker run -d -p 1389:1389 -p 1636:1636 -p 4444:4444 --name opendj local/forgerock