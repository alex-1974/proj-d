## Goal
Qualify whether `proj-d` should become an independent CRS/coordinate-operation
library rather than duplicate `geodesy-d` or embed a PROJ wrapper in Dunia.

## Inputs
README, ROADMAP, RESEARCH, the workspace contracts, and `geodesy-d` README.

## Deliverables
- [ ] Precise `geodesy-d`/`proj-d`/`imagery-d`/georeferencing boundary.
- [ ] PROJ, pyproj, EPSG, OGC WKT2/PROJJSON and existing-D-binding audit.
- [ ] Resource/axis/unit/epoch/vertical/accuracy/area-of-use contracts.
- [ ] Verified 4326↔3857 and 4326↔UTM correctness + adverse cases.
- [ ] Deterministic missing-grid and context/thread lifetime tests.
- [ ] Decision: standalone package vs binding/adapter vs defer, with reasons.
