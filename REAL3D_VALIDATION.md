# Real3D validation status — v2.0.0-alpha1

## Baseline

The user-supplied v1.0.1 source contained Gradle Wrapper, tests and prior validation evidence. This
branch was created directly from that archive; no application rewrite was performed.

## Checks completed in this workspace

- `tools/verify_project.py`: PASS after adding Real3D checks.
- Kotlin bracket/structure checks: PASS through the project verifier.
- Real3D pure-model tests added for:
  - metric wall geometry,
  - hosted door opening geometry,
  - multi-floor elevation,
  - conduit diameter conversion.
- SceneView 2.3.0 API usage was aligned against the v2.3.0 upstream source/API documentation.

## Build limitation in this workspace

A Gradle test/build attempt was made, but the sandbox cannot resolve `services.gradle.org`, so the
Gradle 8.9 distribution and the new SceneView dependency cannot be downloaded here. The failure is
network/DNS related and occurs before Kotlin compilation.

The existing GitHub Actions workflow has been updated to run the project verifier before Android
unit tests, lint and release assembly. An online Work/GitHub Actions environment should therefore
perform the definitive compile test of this Real3D branch.

## Important

This alpha establishes a real Filament scene graph and real metric geometry. It is not yet the
photorealistic reference target: device/furniture GLB assets, textured PBR materials, curved conduit
elbows and boolean wall chases remain later Real3D milestones.
