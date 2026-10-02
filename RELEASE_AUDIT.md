# Release audit

Release: **v1.0.0**  
Audit date: **2026-10-01**

Local static tests validate the repository layout and scorer pin. GitHub Actions has two release gates: static layout tests and a Docker build followed by `python scripts/smoke_test.py` inside the built image. The smoke test constructs synthetic H5ADs and invokes the real `veckit==0.1.2` scorer. No Challenge data is bundled.

## Current verification

Local: 3/3 static repository tests passing; CI additionally builds the Docker image and runs the real scorer smoke test inside it.
All Python source compiles successfully in the release workspace.
