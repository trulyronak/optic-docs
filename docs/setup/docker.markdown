---
layout: default
title: Docker
nav_order: 1
description: ""
parent: "Starting your API with Optic"
permalink: /setup/docker
---

# Docker

How to add Optic to a Docker API
{: .fs-5 .fw-300 }

{% include_relative shared.markdown %}

---

### Docker-Compose <span class="label label-green">Supported</span> <span class="label label-green">No Code Changes</span>

**Note**: You must have `docker-compose` version of `2.1` or higher to support variable substituion, which is how we implement Optic in this example. If you'd like to use an earlier version of `docker-compose`, you need to use another way of replacing the host port with the `OPTIC_API_PORT` env variable

#### Before
```yml
version: "3"
services:
  app:
    container_name: app
    restart: always # if the container fails, restart the image
    build: . # build this image using the Dockerfile found in this directory
    ports:
      - "3000:3000" # map host port 3000 to container port 3000
```

#### After
```yml
version: "3"
services:
  app:
    container_name: app
    restart: always # if the container fails, restart the image
    build: . # build this image using the Dockerfile found in this directory
    ports:
      - "${OPTIC_API_PORT:-3000}:3000" # map host port $OPTIC_API_PORT or 3000 to container port 3000
```

**Note**: Your start command should be some variation of `docker-compose up`


Now when Optic runs your start command, your API will start on the port Optic assigns it.


---

{% include_relative shared-check.markdown %}
