---
title: tg-archive
description: Archiving and displaying Telegram channels
published: true
date: 2022-12-13T10:13:37.493Z
tags: tg-archive, docker
editor: markdown
dateCreated: 2022-10-18T20:40:21.360Z
---

# General information

`tg-archive` is a tool for exporting Telegram group chats into static websites,
preserving chat history.

**Our main repo:**
**[git.osintukraine.com/andrzej/tg-archive](https://git.osintukraine.com/andrzej/tg-archive)**

**[Issues and suggestions](https://git.osintukraine.com/andrzej/tg-archive/issues)**

Docker integration:
[README.docker.md](https://git.osintukraine.com/andrzej/tg-archive/src/branch/master/README.docker.md)

Originally created by @knadh: [github.com/knadh/tg-archive](https://github.com/knadh/tg-archive)

## Usage on osintukraine.com

We mainly use `tg-archive` to scrape Telegram channels, archive them and publish
the content as HTML with media files:

- [russia.osintukraine.com](https://russia.osintukraine.com/) from
  [t.me/telehunt_watch](https://t.me/telehunt_watch)
- [ruvideos.osintukraine.com](https://ruvideos.osintukraine.com/) from
  [t.me/video_posts](https://t.me/video_posts)
- [ukraine.osintukraine.com](https://ukraine.osintukraine.com/) from
  [t.me/amplifyukraine](https://t.me/amplifyukraine)
- [uavideos.osintukraine.com](https://uavideos.osintukraine.com/) from
  [t.me/ukrainian_videos](https://t.me/ukrainian_videos)
  
## Using tg-archive as Docker container

In examples below we assume that:
- all files created will be owned by current user, that is why we have `--user="$(id -u):$(id -g)"` in Docker commands
- code is in folder `/home/user/tg-archive`
- main all sites folder is `/home/user/tg-archive/sites`
  This folder will keep all sites in sub-folders, with their DBs, configurations.
- example site created below will be named `test`
- build data will go into folder: `/var/www/public/test`

### Build
1. Get source code and put it into: `/home/user/tg-archive`
2. In terminal `cd` to folder `/home/user/tg-archive`
3. Build `tg-archive` image: 
```bash
docker-compose build
```

### Create new site
1. Make sure folder `/home/user/sites` exists
2. Create default site based on templates
```bash
 docker run --rm --user="$(id -u):$(id -g)" -v /home/user/sites:/sites tg-archive --new --path=/sites/test
```
3. Edit new site configuration, specially set `api_id`, `api_hash` and `group` parameters in file `config.yaml`


### Create session file
Skip this step if file `session.session` you already created before.
Executing below will result in asking you about phone number and code sent you by Telegram
```bash
docker run --rm -it --user="$(id -u):$(id -g)" -v /home/user/sites:/sites tg-archive --config=/sites/test/config.yaml --session=/sites/session.session
```

### Download site data

```bash
docker run --rm --user="$(id -u):$(id -g)" -v /home/user/sites:/sites tg-archive --config=/sites/test/config.yaml --session=/sites/session.session --sync
```


**For media folder placed at build destination to avoid duplicate and copy media files.**
**Before** downloading - create manually folder `/var/www/public/test/media` 
```bash
docker run --rm --user="$(id -u):$(id -g)" -v /home/user/sites:/sites -v /var/www/public/test/media:/sites/test/media tg-archive --config=/sites/test/config.yaml --session=/sites/session.session --sync
```

### Build static site (publish)

```bash
docker run --rm --user="$(id -u):$(id -g)" -v /home/user/sites:/sites -v /var/www/public/test:/sites/test/site tg-archive --config=/sites/test/config.yaml --build
```

**For media folder placed at build destination to avoid duplicate and copy media files.**
```bash
docker run --rm --user="$(id -u):$(id -g)" -v /home/user/sites:/sites -v /var/www/public/test:/sites/test/site -v /var/www/public/test/media:/sites/test/media tg-archive --config=/sites/test/config.yaml --build
```


## CSS notes
- describe the CSS tweaks operated on styles.css and WHY

## JS notes
- describe the JS libraries added on the frontend and WHY
