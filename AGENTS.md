# AGENTS.md

## Cursor Cloud specific instructions

**CosRayModifiedISO** is a pure Python scientific library for computing galactic cosmic ray spectra. No external services, databases, or Docker are needed.

### Lint / Test / Run

| Action | Command |
|--------|---------|
| Lint (critical errors) | `flake8 . --count --select=E9,F63,F7,F82 --show-source --statistics` |
| Lint (all warnings) | `flake8 . --count --exit-zero --max-complexity=10 --max-line-length=127 --statistics` |
| Test | `pytest tests/ -v` |
| Demo / hello-world | `python testRunning.py` |

The CI workflow (`.github/workflows/python-package.yml`) mirrors these commands.

### Caveats

- `numba` JIT-compiles on first invocation, so the first test run or import may be slower (~1-2 s).
- `~/.local/bin` must be on `PATH` for `flake8`, `pytest`, and `pip`-installed scripts to be found (the update script handles this).
- The bundled OULU neutron monitor data (`CosRayModifiedISO/neutronMonitorData/OULUinputData.pkl`, ~88 MB) only covers 1964-04-01 to 2021-01-31; timestamps outside this range will error.
