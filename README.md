# Polygonize

Polygonizes a set of Geometrys which contain linework that represents the edges of a planar graph. It's basically an implementation of [GEOS's Polygonizer](https://github.com/echoz/xlibspatialite/blob/master/geos/include/geos/operation/polygonize/Polygonizer.h).

Although, the algorithm is the same as GEOS, it isn't a literal transcription of the C++ source code. It was rewriten in order to get a more javascript like code.

## JSDoc

```javascript
/** Implementation of GEOSPolygonize function (`geos::operation::polygonize::Polygonizer`).
 *
 * Polygonizes a set of lines that represents edges in a planar graph. Edges must be correctly
 * noded, i.e., they must only meet at their endpoints. LineStrings must only have two coordinate
 * points.
 *
 * The implementation correctly handles:
 *
 * - Dangles: edges which have one or both ends which are not incident on another edge endpoint.
 * - Cut Edges (bridges): edges that are connected at both ends but which do not form part
 *     of a polygon.
 *
 * @param {FeatureCollection<LineString>} geoJson - Lines in order to polygonize
 * @returns {FeatureCollection<Polygon>} - Polygons created
 */
```

## Example

This example is the test found in [`test/in/complex.geojson`](https://github.com/NickCis/polygonize/blob/master/test/in/complex.geojson).


```javascript
const polygonize = require('polygonize'),
    fs = require('fs'),
    input = JSON.parse(fs.readFileSync('./test/in/complex.geojson'));

console.log(JSON.stringify(polygonize(input)));
```

The [input](https://github.com/NickCis/polygonize/blob/master/test/in/complex.geojson) as GeoJson LineString:

![](https://cloud.githubusercontent.com/assets/174561/26525683/c30957de-4335-11e7-8eb9-bf72f268efb8.png)

Turned into [polygons](https://github.com/NickCis/polygonize/blob/master/test/out/complex.geojson):

![](https://cloud.githubusercontent.com/assets/174561/26525695/24f5270c-4336-11e7-9b62-60db8c0c9a28.png)


## Documentation

Implementation of GEOSPolygonize function (`geos::operation::polygonize::Polygonizer`).

Polygonizes a set of lines that represents edges in a planar graph. Edges must be correctly
noded, i.e., they must only meet at their endpoints. LineStrings must only have two coordinate
points.

The implementation correctly handles:

-   Dangles: edges which have one or both ends which are not incident on another edge endpoint.
-   Cut Edges (bridges): edges that are connected at both ends but which do not form part
      of a polygon.

**Parameters**

-   `geoJson` **[FeatureCollection](http://geojson.org/geojson-spec.html#feature-collection-objects)&lt;[LineString](http://geojson.org/geojson-spec.html#linestring)>** Lines in order to polygonize

Returns **[FeatureCollection](http://geojson.org/geojson-spec.html#feature-collection-objects)&lt;[Polygon](http://geojson.org/geojson-spec.html#polygon)>** Polygons created

### Installation

Install this module individually:

```sh
$ npm install polygonize
```
