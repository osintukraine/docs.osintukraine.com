---
title: Baserow
description: Baserow
published: true
date: 2022-10-23T13:55:30.112Z
tags: baserow
editor: markdown
dateCreated: 2022-10-18T21:21:35.860Z
---

## N8N & Baserow
**How to map N8N fields to Baserow tables**  
Auto-mapping is not the way to go for some reason, the best is to name each of
the fields from the JSON document that you need to collect and map them exactly
the same on the Baserow database side, pay attention to column format (mainly
for dates or numbers) in some case, a pure text field is the simplest way to go
to avoid messing around with column formats and date specifications.

You can then drag & drop the JSON documents keys you need and associate it to each baserow field in the N8N baserow node. 

## Preview 
[Ukraine](/https://db.osintukraine.com/public/grid/vw0suabvgKtxZQ5Na_Y9vQsa3mCzU3-Zq3rVRuU9UD4)
[Russia](https://db.osintukraine.com/public/grid/8NRIJOd7hT3V7NbjxRKivwc4Ypqgz0hI1nz3wZgrmT4)

### todo :
- generate media preview for each row
## How to use Baserow for collaboration

### Disinformation
- (wip) labeling Mis/Disinformation with a team

### Geolocation collaboration
- (wip) Kanban view of the incoming new translations/media files that can be used to work on geolocation efforts by different teams. 
### Hate tracker
- mapping hate keywords used to amplify hate or propagate targeted harrassement 
[Live tool](https://osintukraine.com/hate-scraper/)