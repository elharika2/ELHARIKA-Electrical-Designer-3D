# RC3 Validation

## Passed in this environment
- `tools/verify_project.py`: PASS (14 Kotlin files checked)
- `tools/validate_electrical_assets.py`: PASS (15/15 GLB files present)
- Source package integrity check: required before delivery

## Full Android compilation
A direct Gradle 8.9 download was attempted again and failed because this execution environment cannot reach the Gradle distribution host. Therefore RC3 is **not claimed as APK-compiled here**.

The included GitHub Actions workflow now runs:
- structural verifier
- GLB validator
- clean
- unit tests
- lintDebug
- assembleDebug
- assembleRelease

and uploads APK artifacts.
