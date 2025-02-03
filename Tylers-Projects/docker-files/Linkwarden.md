---
title: Linkwarden
description: link warden config
published: true
date: 2025-02-03T00:40:19.136Z
tags: 
editor: markdown
dateCreated: 2025-02-03T00:39:27.865Z
---

# Linkwarden config
To start with I aquired the linkwarden docker compose file from the official linkwarden github repo,
https://github.com/linkwarden/linkwarden/blob/main 


~~~~
version: "3.5"
services:
  postgres:
    image: postgres:16-alpine
    env_file: .env
    restart: always
    volumes:
      - /docker/linkwarden/pgdata:/var/lib/postgresql/data
  linkwarden:
    env_file: .env
    environment:
      - DATABASE_URL=postgresql://postgres:${POSTGRES_PASSWORD}@postgres:5432/postgres
    restart: always
    # build: . # uncomment this line to build from source
    image: ghcr.io/linkwarden/linkwarden:latest # comment this line to build from source
    ports:
      - 3000:3000
    volumes:
      - /docker/linkwarden/data:/data/data
    depends_on:
      - postgres
~~~~

Here is the configuration i used in portainer to create the image. The only major modifications i made were the volumes locations. Rather than setting them to be ./linkwarden, i changed the location to live in /docker/linkwarden. I also am making this public facing so i will be able to access my link storage from all of my devices. To ensure security I have made a reverse proxy configuration for linkwarden which enables and maintains a secure connection to the appliaction. Also i have created my own user then modified my docker environment variables so that no new users can be created without my permission. 

Due to the new format of docker compose stacks within portainer, i was able to remove the version line from the configuration as it was no longer needed. 