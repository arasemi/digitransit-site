---
title: Address search
---

Address search can be used to search addresses. Duh.

<!--
## Address search APIs

Address search can be done using either **Autocomplete API** or **Search API**

Autocomplete API is lighter and it's designed for "autocomplete" style searches. Search API has more search parameters available.

### Which one should I use?

If you need to limit your searches to some area, use Search API. If you don't want to limit searches to some area, use Autocomplete API.

## Autocomplete API
Autocomplete API can be used to make fuzzy searches e.g. when the user starts typing location into a search field. API is available at:

> http://api.digitransit.fi/geocoding/v1/autocomplete

Search for kamppi:
```
curl "http://api.digitransit.fi/geocoding/v1/autocomplete?text=kampp"
```

### Focus Autocomple API responses around given point

Search focus point boosts addresses found near the given focus point.

You can use focus.point-params like so:
```
curl "http://api.digitransit.fi/geocoding/v1/autocomplete?text=kamppi&focus.point.lat=60.1995&focus.point.lon=24.9363"
```

To Read more about Pelias autocomplete API, check:
> https://github.com/pelias/pelias-doc/blob/master/autocomplete.md

-->

### Search API
Search API provides a way query addresses and POIs (points of interest). API is available at:

> http://api.digitransit.fi/geocoding/v1/search

Supported url parameters:
| Parameter       | Type           | Description                                              |
|-----------------|----------------|----------------------------------------------------------|
| text            | string         | Text to be searched
| size            | int            | How many results to return
| boundary.rect   | object         | Search only inside given rectangle
| boundary.cirlce | object         | Search only inside given circle


### Search 'kamppi', return only one result

```
curl "http://api.digitransit.fi/geocoding/v1/search?text=kamppi&size=1"
```

### Restrict searches to given rectangle

```
curl "http://api.digitransit.fi/geocoding/v1/search?text=kamppi&boundary.rect.min_lat=59.9&boundary.rect.max_lat=60.45&boundary.rect.min_lon=24.3&boundary.rect.max_lon=25.5"
```

### Search inside rectangle

```
curl "http://api.digitransit.fi/geocoding/v1/search?text=kamppi&boundary.circle.lat=60.2&boundary.circle.lon=24.936&boundary.circle.radius=30"
```

### Extra documentation

Geocoding API is implemented using Pelias. If you are interested, you can learn more about Pelias search API from:

> https://github.com/pelias/pelias-doc/blob/master/search.md