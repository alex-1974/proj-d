# Domain boundary proposal — not an accepted ADR

- `geo-d`: CRS-independent geometry.
- `geodesy-d`: bounded, verified geodetic and projection **mathematics**;
  already contains Pseudo-Mercator, TM, UTM/UPS and more. Do not duplicate.
- `proj-d` candidate: CRS definition/registry, WKT2/PROJJSON, coordinate
  operation search and prepared transformations, grid/resource and context
  lifetimes, exact error/accuracy policy; possible focused PROJ integration.
- `locationref-d` (planned): discrete location codes (MGRS/Geohash/OLC), not
  general CRS transformations.
- `imageio-d` candidate/GDAL adapter: read geospatial metadata from encoded
  datasets; no invented coordinate operations.
- `imagery-d`: preserve image/scene spatial metadata and request the correct
  mapping onto a target image grid; do not implement its own CRS engine.
- Application/geospatial adapter: connect image geotransform and CRS data to
  CRS transforms and raster resampling.

Open question: generic pixel-to-world affine geotransform type ownership.
It may remain in a small adapter or be promoted to an existing domain library
only after genuine reuse and contract tests. A CRS alone is not georeferencing.
