# VEC ReproBox

**A reproducible VEC environment you can start before debugging Python packaging.**

ReproBox packages the public local scorer and the standard scientific Python stack into a Docker image and VS Code devcontainer. The scorer is pinned to **`veckit==0.1.2`**, the current PyPI release in the 2026-10-01 source snapshot.

## Fastest path

Requirements: Docker Desktop / Docker Engine.

```bash
git clone <this-repository>
cd vec-reprobox
make smoke
```

`make smoke` builds the image and runs a real synthetic T1 H5AD through the installed public `veckit` scorer. A passing smoke test proves more than imports: AnnData write/read, the scorer CLI, the Python API, DE/direction/distribution/co-variation metrics, and core compiled dependencies all execute inside the container.

## Start JupyterLab

```bash
make lab
```

Open the Jupyter URL/token printed by the container. The repository is mounted at `/workspace`, so notebooks and scripts you create persist on the host.

## VS Code / Cursor devcontainer

Open the repository in a client supporting the Dev Containers specification and choose **Reopen in Container**. `.devcontainer/devcontainer.json` uses the exact same Dockerfile and runs the smoke test after creation.

## What's inside

- Python 3.11 on Debian bookworm-slim;
- `veckit==0.1.2` pinned exactly;
- bounded AnnData/NumPy/SciPy/pandas/scikit-learn/h5py versions;
- JupyterLab 4.x;
- Git and CA certificates;
- a non-root `vec` user;
- synthetic end-to-end scorer smoke test;
- Docker Compose and devcontainer entry points.

## Why top-level dependencies are bounded instead of freezing every wheel

The scorer version is part of the evaluation contract and is pinned exactly. Scientific dependencies are bounded below known-compatible versions and below their next major API break. That allows security/bug-fix releases across platforms while preventing an accidental NumPy/AnnData major-version jump. The CI image build is the executable compatibility check.

To record the exact resolved environment of a built image:

```bash
docker run --rm vec-reprobox:local python scripts/versions.py
```

## Data

**No VEC data is included.** Mount or download your own authorized files. ReproBox does not alter Challenge access rules and does not contain validation/test targets.

See `docs/SOURCES.md` for the official source snapshot.
