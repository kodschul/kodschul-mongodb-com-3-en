
## Using geodata in MongoDB

MongoDB provides comprehensive support for geographic data and spatial queries through its geospatial indexing. This enables developers to efficiently store, process and query location data. This course covers the basics of using geospatial data in MongoDB, including how to store, query and process spatial information.

### Basic spatial data types

MongoDB supports several geospatial data types, including:

- **Point (Point)**: A single location in space, defined by latitude and longitude.
-  Line (LineString)**: A series of points that form a straight line or path.
- **Polygon**: A closed shape defined by a series of points representing areas.

### Saving geodata

To save geodata in MongoDB, use the GeoJSON format, which is a standard method for representing geographic data.

#### Example: Saving a point

```javascript
db.places.insertOne({
  name: “Central Park”,
  location: {
    type: “Point”,
    coordinates: [-73.968285, 40.785091] // [longitude, latitude]
  }
});
```

In this example, a location (“Central Park”) with a point is saved in GeoJSON format.

### Geospatial indexing
To perform efficient spatial queries, you need to create a geospatial index on the geodata. MongoDB supports different types of geospatial indexes:

2dsphere Index: supports queries on geospatial data in GeoJSON format.
2d Index: Supports queries on geographic data in the Cartesian coordinate system.
Example: Creating a 2dsphere index

```javascript
db.places.createIndex({ location: “2dsphere” });
```

```javascript
db.places.insertOne({
  name: “Central Park”,
  location: {
    type: “Point”,
    coordinates: [-73.968285, 40.785091] // [longitude, latitude]
  }
});
```

This index enables quick spatial queries on the location field.

### Geospatial queries
MongoDB offers various query methods for processing and analyzing geospatial data:

1. find nearby locations
To find locations that are close to a specific point, use the $near operators.

```javascript
db.places.find({
  location: {
    $near: {
      $geometry: {
        type: “Point”,
        coordinates: [-73.968285, 40.785091]
      },
      $maxDistance: 5000 // Distance in meters
    }
  }
});

```

This query finds locations within a radius of 5 kilometers around the specified point.

2. find locations within a specific polygon
To find locations that are within a specific polygon, use the $geoWithin operator.

```javascript
db.places.find({
  location: {
    $geoWithin: {
      $geometry: {
        type: “Polygon”,
        coordinates: [[
          [-74, 40],
          [-74, 41],
          [-73, 41],
          [-73, 40],
          [-74, 40]
        ]]
      }
    }
  }
});

```

This query finds locations within the specified polygon.

3. calculate distance between two points
To calculate the distance between two points, use the $geoNear aggregation.


```javascript
db.places.aggregate([
  {
    $geoNear: {
      near: {
        type: “Point”,
        coordinates: [-73.968285, 40.785091]
      },
      distanceField: “distance”,
      spherical: true
    }
  }
]);

```

This aggregation calculates the distance between the given point and the stored locations.

