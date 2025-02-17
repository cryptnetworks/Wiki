---
title: Shlink (Link Shortener)
description: The best selfhosted link shortener to serve shortened links to users.
published: true
date: 2025-02-17T15:21:18.469Z
tags: docker, shlink, selfhosted, docker compose, cloud hosted
editor: markdown
dateCreated: 2025-02-17T15:21:18.469Z
---

# Shlink - The absolute best link shortener!



## What is Shlink?
Shlink is an opensource project created by [Alejandro Celaya](https://github.com/acelaya), a full stack developer for Hypothesis (at the time of writing). The slogan of the application reads, ***Keep control over all your shortened URLs, by serving them under your own domains, using this simple yet powerful tool.*** 

It allows for the use of CLI and REST API calls to complete generation through other applications when needed. Utilizing something like Shlink will allow me to generate quick links when posting here and share them out to users across the web with ease.

## My Use Case

I've needed a way to generate links without the slow propagation times of creating a 301 redirect in Cloudflare. This tool will allow for quick generation and will auto handle any new propagation of records seemlessly and instaneously. This will be particularly useful when linking to documentation, presentations, and research completed by myself.

## Installation

1. I started by launching my docker box in Hetzner and navigating to the Portainer page where I can manage my containers.

![screenshot_2025-02-17_at_10.07.53.png](/assets/screenshot_2025-02-17_at_10.07.53.png){.align-left}


2. Under "*Local*", select "*Stacks*"
![screenshot_2025-02-17_at_10.10.11.png](/assets/screenshot_2025-02-17_at_10.10.11.png){.align-left}

3. From there, add a new stack by clicking "*Add Stack*" in the top right.

4. You have some options here. Often times, you'll want to just add from the web editor and paste in whatever config the app gives you, other times you can download and upload to Portainer. In most cases, I like to pull from GitHub and use some basic GitOps to track changes and updates to my application. However, I'm just going to use the Web editor.

![image.png](/assets/image.png)

5. Using the yaml file below, take and paste this into the editor.

```version: '3.8'

services:
  shlink:
    image: shlinkio/shlink:latest
    container_name: shlink
    restart: unless-stopped
    depends_on:
      - postgres
    environment:
      - DEFAULT_DOMAIN=yourdomain.com
      - IS_HTTPS_ENABLED=true
      - GEOLITE_LICENSE_KEY=your_license_key  # Optional, for GeoLite2 support
      - DB_DRIVER=postgres
      - DB_HOST=postgres
      - DB_PORT=5432
      - DB_USER=shlink
      - DB_PASSWORD=shlinkpassword
      - DB_NAME=shlink
    ports:
      - "8080:8080"
    networks:
      - shlink-network

  postgres:
    image: postgres:15
    container_name: shlink-postgres
    restart: unless-stopped
    environment:
      - POSTGRES_USER=shlink
      - POSTGRES_PASSWORD=shlinkpassword
      - POSTGRES_DB=shlink
    volumes:
      - /docker/shlink/db:/var/lib/postgresql/data
    networks:
      - shlink-network

networks:
  shlink-network:
```

