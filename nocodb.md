---
title: NocoDB
description: 
published: true
date: 2023-02-16T11:32:26.636Z
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
API for telehunt 🇷🇺
API for AmplifyUkraine 

(Cannot be used without Authorization token,get in touch if you want to collaborate) 


## Media Previews

- todo : find a way to concatenate two columns fields that contains all the data to have a new field that would generate the media preview on every rows

<iframe
class="nc-embed"
src="https://nocodb.osintukraine.com/dashboard/#/base/feaeed25-434c-46ee-b1dc-64e24422d002?embed"
frameborder="0"
width="100%"
height="700"
style="background: transparent; border: 1px solid #ddd"></iframe>