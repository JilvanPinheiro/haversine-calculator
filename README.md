# Haversine Calculator
This is a simple module to help you determine the great-circle distance between two points on a sphere given their longitudes and latitudes o a geojson file. 

## The formula
This uses the ‘haversine’ formula to calculate the great-circle distance between two points – that is, the shortest distance over the earth’s surface – giving an ‘as-the-crow-flies’ distance between the points (ignoring any hills they fly over, of course!).

Haversine: 	a = sin²(Δφ/2) + cos φ1 ⋅ cos φ2 ⋅ sin²(Δλ/2)
c

formula:
c = 2 ⋅ atan2( √a, √(1−a) )
d = R ⋅ c

where 	φ is latitude, λ is longitude, R is earth’s radius (mean radius = 6,371km); The angles need to be in radians to pass to trig functions.

## Installation
`$ npm install haversine-calculator

## Usage of this module
### haversine (start, end, options)

    const haversine = require('haversine')

    const start = {
      latitude: 30.849635,
      longitude: -83.24559
    }

    const end = {
      latitude: 27.950575,
      longitude: -82.457178
    }

    console.log(haversine(start, end))
    console.log(haversine(start, end, {unit: 'mile'}))
    console.log(haversine(start, end, {unit: 'meter'}))
    console.log(haversine(start, end, {threshold: 1}))
    console.log(haversine(start, end, {threshold: 1, unit: 'mile'}))
    console.log(haversine(start, end, {threshold: 1, unit: 'meter'}))


#### api
- `options.unit` - Unit of measurement applied to result (default `km`, available `km, mile, meter, nmi`)
- `options.threshold` - If passed, will result in library returning `boolean` value of whether or not the start and end points are within that supplied threshold.  (default `null`)
- `options.format` - The format of start and end coordinate arguments. See table below for available values. (default `null`)

| Format        | Example
| ------------- |--------------------------|
| `undefined` (default) | `{ latitude: 30.849635, longitude: -83.24559] }`
| `[lat,lon]`   | `[30.849635, -83.24559]`
| `[lon,lat]`   | `[-83.24559, 30.849635]`
| `{lat,lon}`   | `{ lat: 30.849635, lon: -83.24559] }`
| `geojson`     | `{ type: 'Feature', geometry: { coordinates: [-83.24559, 30.849635] } }`


[MIT License](http://opensource.org/licenses/MIT)