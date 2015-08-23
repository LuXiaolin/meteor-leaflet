# Leaflet for Meteor

## Purpose

To provide a Meteor package to quickly build real-time cross-platform map apps.

## Demo
Meteor Leafet Demo  |  [GitHub](https://github.com/bevanhunt/meteor-leaflet-demo)  |  [Demo](http://leaflet.meteor.com)

## Packaged Libraries
- Leaflet: 1.0.0-beta.1
- Leaflet Providers: 1.1.1
- Leaflet Spin: 0.1.0

## Roadmap
[Estimated Release Schedule](https://github.com/bevanhunt/meteor-leaflet/milestones)

## Usage
- add this package to your Meteor project
  ```bash
    meteor add bevanhunt:leaflet
  ```

- add a map div to html
  ```html
    <div id='map'></div>
  ```

- in Javascript client-side code define Leaflet map with default image path

  ```javascript
    if (Meteor.isClient) {
      L.Icon.Default.imagePath = 'packages/bevanhunt_leaflet/images';
      var map = L.map('map');
    }
  ```

- in Javascript client-side code use a free tile provider [optional] - [Read Docs](https://github.com/leaflet-extras/leaflet-providers)

  ```javascript
    if (Meteor.isClient) {
      L.tileLayer.provider('Thunderforest.Outdoors').addTo(map);
    }
  ```

- in Javascript client-side code use Leaflet Spin [optional]

  - to start the loading spinner
    ```javascript
      if (Meteor.isClient) {
        map.spin(true);
      }
    ```

  - to stop the loading spinner
    ```javascript
      if (Meteor.isClient) {
        map.spin(false);
      }
    ```

- Create Reactive Popups - for more [info on Blaze.renderWithData](http://docs.meteor.com/#/full/blaze_renderwithdata) [optional]
  ```javascript
    var marker = L.marker([50.5, 30.5]).addTo(map);
    // wrapping node for bindPopup
    var containerNode = document.createElement('div');
    // Which template to use for the popup? Some data for it, and attach it to the containerNode
    Blaze.renderWithData(Template.popup, dataContext, containerNode);
    // Finally bind the containerNode to the popup
    marker.bindPopup(containerNode).openPopup()
  ```

## GeoJSON

### From Arrays
* [meteor-leaflet-demo geojson branch](https://github.com/bevanhunt/meteor-leaflet-demo/tree/geojson) is an example array conversion app using the [geojson npm package](https://www.npmjs.com/package/geojson).

### From KML/GPX
* [meteor-leaflet-demo KML branch](https://github.com/bevanhunt/meteor-leaflet-demo/tree/kml) is a example KML conversion app using the [togeojson npm package](https://www.npmjs.com/package/togeojson).

### From other Formats
* [Orge Web Service](http://ogre.adc4gis.com/) can be used for straight conversion.

## License
MIT
