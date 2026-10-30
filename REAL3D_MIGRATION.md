# ELHARIKA Real 3D migration — v2.0.0-alpha1

This branch keeps the validated v1.0.1 editor, project model, S Pen workflow, circuits,
routing, simulation, persistence and exports intact. Only the 3D rendering path is extended.

## Engine choice

- SceneView 2.3.0
- Google Filament 1.56 (transitive through SceneView)
- Existing project toolchain preserved: AGP 8.7.3, Kotlin 2.0.21, Java 17, compileSdk 35.

SceneView 4.x was intentionally not used in this first migration because its current releases
require a substantially newer Android/Kotlin/JDK toolchain. Once the Real3D bridge is stable,
the renderer can be upgraded independently.

## Architecture

`ElectricalProject -> Real3DSceneBuilder -> Real3DPrimitive -> SceneView/Filament`

The 2D editor stays the source of truth. No separate 3D project format is introduced.

## Implemented in alpha1

- Real perspective camera with orbit/pan/zoom through SceneView.
- True volumetric wall geometry using real metric wall thickness and ceiling height.
- Wall splitting around hosted doors and windows, producing actual rectangular openings.
- Real floor slabs from ROOM bounds.
- Real 3D door/window frames.
- Real conduit tubes and vertical drops/rises.
- Saignée visualization as separate 3D geometry.
- Individual L/N/PE conductor tubes.
- Device boxes, sockets/switch placeholders, lights, contactors, panels and risers as 3D meshes.
- Multi-floor elevation support.
- Current-floor/all-floor filtering.
- Circuit isolation.
- Opaque/transparent/hidden walls.
- Cutaway filtering.
- Existing construction stages reused in Real3D.
- Legacy pseudo-3D retained as fallback.

## Not yet final

- Imported photorealistic GLB assets for sockets, switches, panels and furniture.
- Boolean wall chases (alpha1 renders chases as geometry on/inside the wall surface).
- Curved elbows generated as torus/bend meshes; current conduits are straight cylinders per segment.
- Automatic UV/textures/material library.
- Runtime asset catalog and manufacturer models.
- Full APK build validation of this Real3D branch in an online Android build environment.

## Licensing

SceneView is Apache-2.0. Any third-party GLB assets added later must have compatible licenses and
must be tracked in an asset attribution manifest.
