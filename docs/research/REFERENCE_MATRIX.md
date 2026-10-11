# CRS reference matrix — research starting point

| Reference | What to inspect | Caveat |
|---|---|---|
| PROJ | Contexts, CRS DB, WKT/PROJJSON, operations, grids, C ABI | Native binary + versioned proj.db/grids |
| pyproj | Human-friendly D candidate API ergonomics, operation info, always_xy | Python convenience does not define D semantics |
| EPSG/IOGP | Datum/CRS/coordinate-operation definitions, methods | Registry versions and licensing |
| OGC WKT2 / ISO 19111 | Standardized CRS metadata models | Scope and complexity |
| geodesy-d | Existing D types, frames, projection mathematics | Avoid duplicate implementation / coupling |
| GDAL/GeoTIFF | Pixel-to-world geotransform and CRS metadata | Georeferencing is not identical to a CRS |

Primary sources:
- https://proj.org/en/stable/development/reference/functions.html
- https://proj.org/en/stable/resource_files.html
- https://epsg.org/
- https://www.ogc.org/standards/wkt-crs/
- https://pyproj4.github.io/pyproj/stable/api/transformer.html
- https://gdal.org/en/stable/tutorials/geotransforms_tut.html

Pin versions, database snapshots and grids during the first experiment.
