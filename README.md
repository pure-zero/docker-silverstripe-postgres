# SilverStripe Development Environment

This repository is designed to be used with SilverStripe development environments. 
It contains packages and functionality commonly used when developing with SilverStripe.

You'll need docker and docker-compose installed to get this running

Thanks to Brett Tasker for providing the base to this repo https://github.com/brettt89/silverstripe-docker/tree/3

I just added replaced mysql for postgres in the setup

## Requirements

 * [Docker](https://docs.docker.com/engine/installation/)
 * [Docker Compose](https://docs.docker.com/compose/install/#install-compose)

##### Applications packaged in docker-compose.yml

 * Apache Webserver
 * Postgres Database
 * Composer
 * SSPAK

### Setup

These commands should be run from within the project folder created during Installation.

*E.g. `./my/website/folder`*

##### Clone website into `public/` directory
```bash
git clone <repo> public
```
*NOTE: It is important that the website codebase exists in the `public/` directory* 


##### Install composer dependencies:
```bash
docker-compose run composer install
```

##### Import database with sspak:

*NOTE: Copy your sspak into the `snapshots/` directory* For iPayroll this is done already, please update this as you see fit
```bash
docker-compose run sspak load snapshots/dev.sspak public
```

##### Finally, bring up the site and the asset builder:
```bash
docker-compose up -d web
```
The asset builder uses gulp to watch the swift directory for any changes and 
rebuilds as necessary

**The site will then be available at http://localhost/.**

You may need to run a dev build before everything is up and running perfectly 

http://localhost/dev/build?flush=all