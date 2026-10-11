# CRS / georeferencing research questions

This is a research backlog, not an accepted public API.

| Question | Necessary evidence |
|---|---|
| What is the correct meaning of an EPSG code? | Versioned registry/db semantics, units, axes, datum, area of use |
| How are CRS strings parsed? | WKT2/PROJJSON round-trip and unsupported cases |
| Which coordinate operation is selected? | AOI, accuracy, available grids, ballpark fallback policy |
| Which axis order is accepted at the public boundary? | EPSG authority axis conventions vs explicit GIS XY mode |
| How do we handle epochs and vertical coordinates? | Concrete dynamic/vertical source + target examples |
| What fails when a grid file is missing? | Error propagation, no silently approximate operation |
| Who owns PROJ context and operation handles? | Lifetime, thread isolation, `@safe` consumer boundary |
| Where does raster georeferencing belong? | Pixel-space, geotransform and CRS coupling without mixing owners |
| Is standalone `proj-d` justified? | Real consumers, alternate designs, maintenance costs |

Do not assert transformation correctness merely from round trips; compare
against independent tools or normative EPSG example data, including adverse
regions and boundary/axis cases. Record resource and database versions.
