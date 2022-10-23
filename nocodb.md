---
title: NocoDB
description: 
published: true
date: 2022-10-23T13:48:52.620Z
tags: nocodb, nocode, api
editor: markdown
dateCreated: 2022-10-22T20:25:56.948Z
---

# NocoDB
[Instance ](https://nocodb.osintukraine.com/dashboard/)

## SQLite integration in cloudron context
![sqlitemount.png](/sqlitemount.png)
- each sqlite file is symlinked to /srv/
![2022-10-23_15-34.jpg](/2022-10-23_15-34.jpg)
- each sqlite file is mounted as an external volume
- each of these volumes can be tied to a container, allowing any app to access the entire media aggregation being served by the static sites. 
![2022-10-23_15-37.jpg](/2022-10-23_15-37.jpg)

## API provider
API for telehunt [Telehunt](https://nocodb.osintukraine.com/api/v1/db/meta/projects/p_cpo18cl23r0sq4/swagger) 🇷🇺

(Cannot be used without Authorization token,get in touch if you want to collaborate) 


## Media Previews

- todo : find a way to concatenate two columns fields that contains all the data to have a new field that would generate the media preview on every tables