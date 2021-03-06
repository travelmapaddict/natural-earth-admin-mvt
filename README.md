# Natural Earth Admin features in Mapbox Vector Tile format

## Quickstart

From the root of the repository, run:

```sh
make
```

This will produce a file in the repository root, `ne-admin.mbtiles`, which can be served with [your favorite mvt server](https://github.com/mapbox/awesome-vector-tiles#servers).

## Available `make` commands

### `make`/`make all`/`make ne-admin.mbtiles`

Create the file `ne-admin.mbtiles`, which is a bundled package of [Mapbox Vector Tiles](https://www.mapbox.com/vector-tiles/).

#### Prerequisites

You'll need to have already installed [curl](https://curl.haxx.se/), [jq](https://stedolan.github.io/jq/), [tippecanoe](https://github.com/mapbox/tippecanoe), and [tileserver-gl-light](https://www.npmjs.com/package/tileserver-gl-light) on your machine.

#### Data

Features are sourced from the [10m Natural Earth Admin 0 and Admin 1 geojson](https://github.com/nvkelso/natural-earth-vector/tree/master/geojson). Major lakes straddling international boundaries are excluded from the features. All features are rendered as polygons/multipolygons in the vector tiles. Zoom levels 0 thru 5 are rendered.

#### Layers

Features in the vector tiles are organized into two layers:

* `admin-0`: All Admin 0 features. Rendered into all zoom levels.
* `admin-1`: All Admin 1 features. Rendered into zoom levels 3-5.

#### Tags

All features have two tags. Tag values are pulled from Natural Earth data.
* `name`: a human-readable, generally english-language field
* `iso`: The [ISO 3166-1](https://en.wikipedia.org/wiki/ISO_3166-1) Alpha 2 code for the `admin-0` features, and the [ISO 3166-2](https://en.wikipedia.org/wiki/ISO_3166-2) code for the `admin-1` features.

Note that not all features have ISO 3166 codes defined in Natural Earth. Notable exceptions include, as of this writing, Norway and France.

### `make serve`

Start up a webserver ([tileserver-gl-light](https://www.npmjs.com/package/tileserver-gl-light)) to allow you to visually inspect your local `ne-admin.mbtiles`. While running the webserver in a terminal window, load http://localhost:8080/ in a browser. To quit the webserver, use `ctrl-c`.

### `make clean`

Delete all final and intermediate data products, excluding the raw downloads of Natural Earth data.

### `make fullclean`

Everything `make clean` does, and also delete the raw downloads of Natural Earth data.

## Contributing

Bugs, feature suggestions - please file a github issue or make a pull request.

## License

[MIT](https://github.com/travelmapaddict/natural-earth-admin-mvt/blob/master/LICENSE)
