# Static website for *morton.dev*

[![Laravel Forge Site Deployment Status](https://img.shields.io/endpoint?url=https%3A%2F%2Fforge.laravel.com%2Fsite-badges%2Ffda07f2e-8158-4b64-9015-67c2af393b76%3Fdate%3D1%26label%3D1%26commit%3D1&style=plastic)](https://forge.laravel.com/servers/872762/sites/2581229)

This repo contains a static single page website for morton.dev.

## Original README


This repo contains a docker-compose.yml that creates a static website and a Traefik reverse proxy. It was created to test the Traefik reverse proxy with a static website when using Laravel Forge, but it should work for any server that has Docker installed where you are testing Traefik.

It was created to be used as a sample web site for the following repo: https://github.com/johnfmorton/traefik-for-laravel-forge

## The accompanying blog post

For a complete write-up on using this repo, read [*Analytics a different way. Plausible Analytics on Laravel Forge with Traefik and Docker.*](https://supergeekery.com/blog/plausible-analytics-on-laravel-forge-with-traefik-and-docker)

## Usage

The repo assumes you have Docker installed and running.

As shown in the reference repo above, it also assumes you have a Traefik container running. The Traefik container should be running on the same network as the containers created by this repo. The Traefik container uses a network called `proxy` by default. If you are using a different network, you will need to update the `docker-compose.yml` file in this repo to use the correct network.

To start the containers, run the following command:

```
docker-compose -p basic-web-site -f docker-compose.yml up -d --remove-orphans
```

## DNS and the environment file

Using the [`example.env`](/example.env) file as a reference, create a `.env` file in the same directory as the `docker-compose.yml` file. The `.env` file should contain the following variables:

```
SITE_URL=example.com
```

You will also need to configure your DNS host to point the domain name to the IP address of the server where the containers are running.

## About the directories

The `web` directory contains the static website files.

The `web` directory is mounted as a volume in the `nginx` container. The `nginx` container is configured to serve the files in the `web` directory. The `index.html` file should display a simple "Hello World" message.

## License

The source code for the site is licensed under the MIT license, which you can find in
the MIT-LICENSE.txt file.
