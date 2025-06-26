# OS-APS Docker Installation

## Requirements

* Install Git: https://git-scm.com/downloads
* Install Docker Desktop: https://www.docker.com/products/docker-desktop/
* Visit: https://os-aps.de/en/

## Install

Clone this repository: `git clone https://github.com/fid-philosophie/bid2025.git`

```
cd bid2025
mkdir osaps_data
cd osaps_data
```

On Linux:

```
docker run \
    --rm \
    -p 127.0.0.1:3000:3000/tcp \
    --platform linux/amd64 \
    --name os-aps-demo \
    --volume "$(pwd):/data" \
    --env LOCAL_STORAGE_PATH=/data/manuscripts \
    --env INSTANCE_TITLE="Bibliothekskongress 2025" \
    --env FONT_PATH=/data/fonts/ \
    --env LOG_LEVEL=debug \
    registry.gitlab.com/sciflow/development/server:latest
```

Linux inline:

```
docker run --rm -d -p 127.0.0.1:3000:3000/tcp --platform linux/amd64 --name os-aps-demo --volume "$(pwd):/data" --env LOCAL_STORAGE_PATH=/data/manuscripts --env INSTANCE_TITLE="Bibliothekskongress 2025" --env FONT_PATH=/data/fonts/ --env LOG_LEVEL=debug registry.gitlab.com/sciflow/development/server:latest
```

On Windows CMD:

```
docker run --rm -d -p 127.0.0.1:3000:3000 --platform linux/amd64 --name os-aps-demo --volume "%CD%:/data" --env LOCAL_STORAGE_PATH=/data/manuscripts --env INSTANCE_TITLE="Bibliothekskongress 2025" --env FONT_PATH=/data/fonts/ --env LOG_LEVEL=debug registry.gitlab.com/sciflow/development/server:latest
```

## Running instance in the browser

http://localhost:3000

## Accessing an existing document

http://localhost:3000/start/quack-frog-7506810a-88fa-4879-b290-6a95347fc327

If you decide to deploy the system to a live server consider using a htaccess password.

## Including Templates

Linux:
```
docker run \
    --rm \
    -p 127.0.0.1:3000:3000/tcp \
    --platform linux/amd64 \
    --name os-aps-demo \
    --volume "$(pwd):/data" \
    --env LOCAL_STORAGE_PATH=/data/manuscripts \
    --env INSTANCE_TITLE="Bibliothekskongress 2025" \
    --env FONT_PATH=/data/fonts/ \
    --env TEMPLATE_SOURCE=/data/templates/ \
    --env LOG_LEVEL=debug \
    registry.gitlab.com/sciflow/development/server:latest
```

```
docker run --rm -d -p 127.0.0.1:3000:3000/tcp --platform linux/amd64 --name os-aps-demo --volume "$(pwd):/data" --env LOCAL_STORAGE_PATH=/data/manuscripts --env INSTANCE_TITLE="Bibliothekskongress 2025" --env FONT_PATH=/data/fonts/ --env LOG_LEVEL=debug --env TEMPLATE_SOURCE=/data/templates registry.gitlab.com/sciflow/development/server:latest
```
## Stop instance

On Docker Desktop, you can stop the running container under ‘Containers’, or you can also stop the instance on command line via `docker stop phidi-osaps`

## Try the new version in the cloud

https://os-aps.sciflow.net/start

## Extra resources

The repository:

https://gitlab.com/sciflow/development

The templates:

https://gitlab.com/os-aps/templates
