---
title: tg-archive
description: Archiving and displaying Telegram channels
published: true
date: 2022-10-18T21:44:42.427Z
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
the content as HTML:

- [russia.osintukraine.com](https://russia.osintukraine.com/) from
  [t.me/telehunt_watch](https://t.me/telehunt_watch)
- [ruvideos.osintukraine.com](https://ruvideos.osintukraine.com/) from
  [t.me/video_posts](https://t.me/video_posts)
- [ukraine.osintukraine.com](https://ukraine.osintukraine.com/) from
  [t.me/amplifyukraine](https://t.me/amplifyukraine)
- [uavideos.osintukraine.com](https://uavideos.osintukraine.com/) from
  [t.me/ukrainian_videos](https://t.me/ukrainian_videos)

### CSS notes
- describe the CSS tweaks operated on styles.css and WHY

### JS notes
- describe the JS libraries added on the frontend and WHY
