[![Build Status](https://travis-ci.org/alekzvik/point-on-earth.svg?branch=master)](https://travis-ci.org/alekzvik/point-on-earth)
[![Coverage Status](https://coveralls.io/repos/github/alekzvik/point-on-earth/badge.svg)](https://coveralls.io/github/alekzvik/point-on-earth)
[![license](https://img.shields.io/github/license/mashape/apistatus.svg)]()
[![PyPI](https://img.shields.io/pypi/pyversions/Django.svg)]()

# point-on-earth
Generate a land point.

## What?
* Generate a point, not in the ocean.

## Why?
Sometimes you just need a point that is not in the water :)

## Examples
Feature
```python
>>> from shapely.geometry import Point
>>> from shapely_geojson import dumps, Feature
>>> feature = Feature(Point(1, 2), properties={'key': 'value'})
>>> print(dumps(feature, indent=2))
{
  "type": "Feature",
  "geometry": {
    "type": "Point",
    "coordinates": [
      1.0,
      2.0
    ]
  },
  "properties": {
    "key": "value"
  }
}
```
FeatureCollection
```python
>>> feature1 = Feature(Point(1, 2), {'index': 1})
>>> feature2 = Feature(Point(3, 4), {'index': 2})
>>> features = [feature1, feature2]
>>> feature_collection = FeatureCollection(features)
>>> for feature in feature_collection:
...     print(feature.properties['index'])
...
1
2
>>> print(dumps(feature_collection, indent=2))
{
  "type": "FeatureCollection",
  "features": [
    {
      "type": "Feature",
      "geometry": {
        "type": "Point",
        "coordinates": [
          1.0,
          2.0
        ]
      },
      "properties": {
        "index": 1
      }
    },
    {
      "type": "Feature",
      "geometry": {
        "type": "Point",
        "coordinates": [
          3.0,
          4.0
        ]
      },
      "properties": {
        "index": 2
      }
    }
  ]
}

```

# Attributions
Uses land polygons from Natural Earth.
