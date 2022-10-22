---
title: TG-Archive
description: tg-archive - how to in the cloudron/docker context
published: true
date: 2022-10-18T21:44:42.427Z
tags: tg-archive, docker
editor: markdown
dateCreated: 2022-10-18T20:40:21.360Z
---

# Using tg-archive as Docker container

In examples below we assume that:
- all files created will be owned by current user, that is why we have `--user="$(id -u):$(id -g)"` in Docker commands
- code is in folder `/home/user/tg-archive`
- main all sites folder is `/home/user/tg-archive/sites`
  This folder will keep all sites in sub-folders, with their DBs, configurations.
- example site created below will be named `test`
- build data will go into folder: `/var/www/public/test`

## Build
1. Get source code and put it into: `/home/user/tg-archive`
2. In terminal `cd` to folder `/home/user/tg-archive`
3. Build `tg-archive` image: 
```bash
docker-compose build
```

## Create new site
1. Make sure folder `/home/user/sites` exists
2. Create default site based on templates
```bash
 docker run --rm --user="$(id -u):$(id -g)" -v /home/user/sites:/sites tg-archive --new --path=/sites/test
```
3. Edit new site configuration, specially set `api_id`, `api_hash` and `group` parameters in file `config.yaml`


## Create session file
Skip this step if file `session.session` you already created before.
Executing below will result in asking you about phone number and code sent you by Telegram
```bash
docker run --rm -it --user="$(id -u):$(id -g)" -v /home/user/sites:/sites tg-archive --config=/sites/test/config.yaml --session=/sites/session.session
```

## Download site data

```bash
docker run --rm --user="$(id -u):$(id -g)" -v /home/user/sites:/sites tg-archive --config=/sites/test/config.yaml --session=/sites/session.session --sync
```


**For media folder placed at build destination to avoid duplicate and copy media files.**
**Before** downloading - create manually folder `/var/www/public/test/media` 
```bash
docker run --rm --user="$(id -u):$(id -g)" -v /home/user/sites:/sites -v /var/www/public/test/media:/sites/test/media tg-archive --config=/sites/test/config.yaml --session=/sites/session.session --sync
```

## Build static site (publish)

```bash
docker run --rm --user="$(id -u):$(id -g)" -v /home/user/sites:/sites -v /var/www/public/test:/sites/test/site tg-archive --config=/sites/test/config.yaml --build
```

**For media folder placed at build destination to avoid duplicate and copy media files.**
```bash
docker run --rm --user="$(id -u):$(id -g)" -v /home/user/sites:/sites -v /var/www/public/test:/sites/test/site -v /var/www/public/test/media:/sites/test/media tg-archive --config=/sites/test/config.yaml --build
```

# Auth
- Get [Telegram API credentials](https://my.telegram.org/auth?to=apps). Normal user account API and not the Bot API.
- Describe auth tips

## Usage

1. `tg-archive --new --path=mysite` (creates a new site. `cd` into mysite and edit `config.yaml`).
1. `tg-archive --sync` (syncs data into `data.sqlite`).
  Note: First time connection will prompt for your phone number + a Telegram auth code sent to the app. On successful auth, a `session.session` file is created. DO NOT SHARE this session file publicly as it contains the API autorization for your account.
1. `tg-archive --build` (builds the static site into the `site` directory, which can be published)
1. describe the changes made in the code to have incremental builds and show_day_index

# Customization
Edit the generated `template.html` and static assets in the `./static` directory to customize the site.

## CSS notes
- describe the CSS tweaks operated on styles.css and WHY

## JS notes
- describe the JS libraries added on the frontend and WHY

# Note
- The sync can be stopped (Ctrl+C) any time to be resumed later.
- Setup a cron job to periodically sync messages and re-publish the archive.
-- Describe the server side cron job setup
- Downloading large media files and long message history from large groups continuously may run into Telegram API's rate limits. Watch the debug output.
-- document experience related to this, distribution of sessions/devices (15min)

Licensed under the MIT license.