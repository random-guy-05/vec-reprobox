# Community Contribution submission text

## Title
VEC ReproBox — one-command Docker/devcontainer environment with a real scorer smoke test

## Description
VEC ReproBox gives participants a reproducible environment instead of only diagnosing a broken one. It provides a Dockerfile, Docker Compose setup and VS Code devcontainer with Python 3.11, the current public scorer pinned at `veckit==0.1.2`, bounded AnnData/scientific dependencies, JupyterLab and Git. `make smoke` builds the image and runs a fully synthetic T1 AnnData prediction/reference/target through the actual installed veckit scorer, checking the CLI, Python API and expected ranking metrics rather than merely testing imports. The image runs as a non-root user and contains no Challenge data. It helps first-time entrants, workshop participants, classrooms and teams reproduce the same working software environment across laptops and cloud machines.
