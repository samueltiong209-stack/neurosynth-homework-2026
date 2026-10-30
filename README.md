# Neurosynth homework backend

Flask + PostgreSQL. Complete source, portable original dataset, setup instructions and verification reports are in `neurosynth_backend.zip` (extracts to backend/).

Render build command:
```sh
python -m zipfile -e neurosynth_backend.zip . && python -m pip install -r backend/requirements.txt
```
Render start command:
```sh
sh backend/start.sh
```
Set DATABASE_URL to the internal URL of a Free PostgreSQL database in the same region. Web service and PostgreSQL must both use Free ($0). Set PYTHON_VERSION=3.14.0 and health check /health.

Dissociate is provisionally A minus B, not an instructor-confirmed statistical definition. The source repository supplied by the instructor returned HTTP 404.

Original notebooks, models, passwords and virtual environments are excluded.
