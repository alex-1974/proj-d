# Roadmap — CRS infrastructure research and gates

## R0 — Scope and georeferencing boundary (CURRENT)

- Compare responsibilities of `geodesy-d`, `proj-d`, `geo-d`, `imagery-d`,
  I/O adapters and `locationref-d`.
- Keep CRS definitions distinct from pixel-to-world image georeferencing,
  projection mathematics and location codes.
- Establish two concrete consumers (e.g. position transform and orthophoto
  placement) without introducing a universal framework prematurely.

## R1 — Primary reference/API audit

Study PROJ C API, pyproj, EPSG/ISO 19111/OGC WKT2, PROJJSON, relevant D
bindings, licensing/data distribution, operation selection and version matrix.

## R2 — Reproducible coordinate-operation contracts

Test at least:
- EPSG:4326 ↔ EPSG:3857, noting official axis order versus GIS XY order;
- EPSG:4326 ↔ UTM (including `geodesy-d` independent comparison);
- compound/vertical and datum-grid-required operations (capability/gap study);
- area of use, epoch/dynamic CRS and missing resource semantics;
- thread/context and native handle ownership;
- N-coordinate batch transforms and error reporting.

Record exact versions, EPSG/proj.db/grids available, axis and unit contracts,
transform selection, operation accuracy claims, result/diagnostic behavior.

## R3 — Admission decision

Document whether a small PROJ C binding plus idiomatic wrapper offers
independent utility. Alternatives: existing D bindings, pure-D limited
functions in `geodesy-d`, application-local adapter or deferral.

An admitted package needs consumer contracts, independent numerical oracles,
DMD/LDC checks, owned-resource/failure/safety proofs and measured performance.

## R4 — Conditional production

Only after explicit decision: introduce a DUB package, public Ddoc,
module root, minimum compiler/native-library versions, tests, release CI,
licence and supported CRS/database/grids policy. Do not silently make
`geodesy-d` depend on PROJ.
