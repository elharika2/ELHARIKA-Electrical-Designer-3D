# ELHARIKA Electrical Designer 3D — v2.0.0-rc2
## RC2 professional tablet UI
- Dark three-column studio interface based on the approved visual direction.
- Real GLB-derived thumbnails in the electrical component library.
- Real3D opens by default with controls moved to the right operations panel.
- One-click Demo House electrical project for immediate 3D evaluation.

## RC1
- Final electrical-installation-focused release candidate.
- Performance / Balanced / Ultra Real3D quality modes.
- 15/15 embedded GLB electrical components.
- Live simulation and close-up installation details retained.

## Alpha 8 close-up electrical realism
- Direction-aware GLB fittings and clamps.
- Real T/cross junction entry counts.
- Cable-entry glands on connected device boxes and panels.

## Alpha 7 live electrical 3D
- Simulation state visible directly on Real3D routes/devices.
- Shared conduit support rails.
- Penetration sleeves/grommets at route endpoints.
- 15/15 embedded electrical GLBs retained.

## Alpha 6 embedded GLB pack
- 15/15 electrical GLB files physically bundled.
- Mobile-first detailed assets for conduits, fittings, boxes, devices and panel hardware.
- Procedural fallback retained.

## Alpha 5 photoreal asset bridge
- GLB asset catalog + automatic fallback.
- Runtime GLB availability counter.
- Electrical asset manifest and license tracking.

## Alpha 4 electrical-installation focus
- Auto junction boxes at route crossings.
- T-branch detection.
- Parallel conduit bundles.
- Vertical-drop elbows and glands.


# ELHARIKA Electrical Designer 3D v2.0.0-alpha1 — Real 3D

> This Real3D branch is built directly on the validated v1.0.1 source supplied by the user. The 2D editor, persistence, circuits, simulation and exports are preserved.

# ELHARIKA Electrical Designer 3D v1.0.1

Patched build of the supplied v1.0.0 source project. See VALIDATION.md for the actual verification results and device checks still required.

## Major capabilities included
- Tablet-first 2D electrical floor-plan editor with S Pen input.
- Smart sketch recognition, walls, rooms, doors, windows, dimensions and CAD editing tools.
- Floors, layers, grouping, selection box, copy/paste and wall/room relationships.
- Electrical devices, circuits, automatic routing, cable quantities, BOM, PDF and CSV export.
- 3D construction/install view with cutaway walls, conduits, saignées, embedded boxes and individual conductors.
- Construction sequence: Tableau → Saignées → Gaines → Boîtes → Fils → Appareils.
- Terminal-to-terminal WireLink network for L/N/PE conductors.
- Wiring validation for continuity and common connection errors.
- Interactive simulation for simple switches, lights, voltage presence, open circuit and short-circuit faults.
- Simplified paired va-et-vient simulation.
- Simplified contactor control using a selected switch or manual coil state.
- Energized-route and lit-lamp visualization in 3D.
- Persistent project data with backward-compatible defaults.

## v1.0 additions
- Va-et-vient design element and pair assignment.
- Two-position va-et-vient simulation. A pair passes live when its positions match.
- Contactor design element.
- Contactor contacts can be controlled by a simple/va-et-vient switch or manual coil state.
- Diagnostics warn about unpaired va-et-vient switches and contactors without a control.
- Dedicated 2D/3D symbols and simulation controls for both device types.
- JUnit model test scaffolding.
- `tools/verify_project.py` structural sanity checker.

## Important simulation note
The simulation is intended for design and training. The va-et-vient and contactor behavior is a simplified logical model and is not a certified protection, selectivity, fault-current or installation-compliance calculation engine.

## Building and validation

Use JDK 17 and Android SDK platform 35. The Gradle 8.9 wrapper is included.

```sh
./gradlew testDebugUnitTest lintDebug assembleRelease
```

On Windows use `gradlew.bat` instead of `./gradlew`.
Without signing environment variables, `assembleRelease` creates an unsigned APK.
To sign with your own retained key, set `ELHARIKA_KEYSTORE` to an absolute path,
`ELHARIKA_STORE_PASSWORD`, and optionally `ELHARIKA_KEY_ALIAS` (default `elharika`)
and `ELHARIKA_KEY_PASSWORD` (defaults to the store password).
Do not commit keystores or passwords. A separate private signing backup is
provided for the APK produced in this review.

## Fixes in this review

- Added the Gradle wrapper, Java/Kotlin 17 compatibility, optional release signing, and a CI workflow.
- Fixed the missing Compose nativeCanvas import and layout API opt-in.
- Corrected two-way switch re-pairing and reference remapping on copying/floor duplication.
- Removed obsolete wiring/state references after device and floor deletion.
- Detect missing socket earth continuity even when no PE wire exists.
- Account for open-circuit faults on cables and refresh enabled simulation after edits.
- Cancel interrupted drawing gestures without committing a wall or cable.
- Count two-way switches, contactors, and junction boxes in the bill of materials.
- Fit large/negative-coordinate plans into PDF pages, paginate long summaries,
  and include the newer electrical device types in plan exports.
- Quote CSV cells, use stable decimal formatting, and neutralize formula-like labels.
- Restore progressive conduit/wire animation and isolate newer device types by circuit.
- Reject invalid drawing scale/grid values that could freeze rendering.

## Visual and simulation scope

The supplied showcase is a design illustration, not a screenshot of this APK.
The current app projects 3D geometry onto a Compose Canvas; it has no photorealistic
materials, furniture models, or physically rendered product models.
The simulation is a simplified connectivity/logical model. It does not solve
real terminal voltages, coil power, current/selectivity or certified fault protection.
The paired two-way switch truth table assumes matching traveller positions.
The app stores one active project locally; it does not provide a multi-project file browser.
S Pen input uses generic stylus events and still requires physical device testing.
Real Galaxy Tab S10+ installation, touch/stylus behavior, screen layout and performance
must be checked separately before describing this release as production-ready.


## Alpha3 focus
See `ELECTRICAL_REALISM_ALPHA3.md`.
