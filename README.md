# proj-d — CRS & coordinate-operation research

**Status: research only — no production package/API admitted.**

This name follows the existing `d-geospatial-workspace` candidate `proj-d`.
The project researches a focused, idiomatic D integration for **coordinate
reference systems (CRS)** and coordinate-operation discovery/execution, with
PROJ as a primary external reference and possible runtime backend.

## Why a separate domain?

`geodesy-d` already implements bounded, validated pure-D Earth/ellipsoid,
projection and geodetic maths. A full CRS system adds authority definitions,
axis order, datum/reference frame identification, WKT/PROJJSON, operations
selected by area/epoch/accuracy, transformation grids/resources and lifecycle
handling. These are distinct responsibilities.

CRS means **Coordinate Reference System**. A CRS definition is not the same as
a raster pixel-to-world geotransform, and neither is the same as a location
code such as Geohash or MGRS. These distinctions are research questions at
the API boundary, not an excuse to consolidate unrelated domains.

## Candidate domain (not accepted API)

- CRS descriptions and identifiers (e.g. EPSG authority/code), WKT2 and
  PROJJSON interchange as supported by a chosen backend.
- Coordinate-operation discovery by source CRS, target CRS, area of interest,
  desired accuracy and available resources, with explicit selection policy.
- Axes, order, angular/linear units, coordinates and dimensions (2D/3D/4D),
  coordinate epoch, vertical and dynamic reference system semantics.
- Operations, prepared transformation lifetimes, errors/accuracy and
  deterministic batch/caller-owned transforms where defensible.
- Context, native PROJ handles, data directory, grids and thread-safety rules.
- Review raster/image georeferencing metadata and geotransform placement;
  coordinate geometry of rasters must not be conflated with CRS parsing.

## Explicit non-goals

- Do not duplicate `geodesy-d` ellipsoidal geodesics, UTM, TM or projections.
- Do not confuse `locationref-d` (MGRS, Geohash, Plus Codes) with CRS.
- Do not introduce image formats or a raster warping engine.
- No own EPSG catalogue copied into the Git repository without clear
  provenance, rights, versioning and demonstrated need.
- No required PROJ dependency for `geodesy-d` or unrelated libraries.

## Preliminary dependency boundary

```text
application / imagery geospatial adapter
       |             |
       v             v
    proj-d       geodesy-d
       |
       v
  optional native PROJ + proj.db + grid resources
```

`proj-d` may reuse existing `geodesy-d` types only if a concrete consumer
justifies the dependency and there is no inversion. Pure D versus a focused
native PROJ binding remains open until research has measured correctness,
coverage, portability and maintenance burden.

## Primary references

- PROJ: https://proj.org/
- PROJ C API: https://proj.org/en/stable/development/reference/functions.html
- PROJ coordinate transformations: https://proj.org/en/stable/operations/index.html
- PROJ resource files: https://proj.org/en/stable/resource_files.html
- EPSG registry: https://epsg.org/
- OGC WKT2 / ISO 19111: https://www.ogc.org/standards/wkt-crs/
- pyproj API / transformer policy: https://pyproj4.github.io/pyproj/stable/api/transformer.html
- Workspace `geodesy-d`: https://github.com/alex-1974/geodesy-d
- Workspace `locationref-d`: planned-design only, not a CRS package.

## Development / activation policy

Current `develop` is research coordination, **not** a released library.
No production `dub.sdl`, `source/` tree, public module root or release baseline
exists. Consult `AGENTS.md`, `ROADMAP.md`, `RESEARCH.md` and the canonical
workspace files before architecture or implementation decisions.
