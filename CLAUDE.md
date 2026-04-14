# rac-us-md

Maryland benefit-program source and encodings live here.

## Scope

- Maryland-administered overlays, manuals, and guidance
- federal program cores remain in `rac-us`
- keep Maryland source slices in this repo even when the underlying program is federal
- Maryland SNAP state-option and self-employment-treatment slices belong here

## Layout

```text
rac-us-md/
├── sources/
│   └── slices/        # exact Maryland source excerpts
└── scripts/
```

## Local commands

```bash
cd /Users/maxghenis/TheAxiomFoundation/rac
uv run python -m rac.validate all /Users/maxghenis/TheAxiomFoundation/rac-us-md
uv run python -m rac.test_runner /Users/maxghenis/TheAxiomFoundation/rac-us-md -v

cd /Users/maxghenis/TheAxiomFoundation/rac-us-md
python3 scripts/validate_repo.py
```

## Encoding policy

- Repo boundaries follow jurisdictions, not program labels.
- Maryland SNAP overlays belong here, not in `rac-us`.
- Preserve exact source slices under `sources/slices/`.
- For delegated state-set parameters, add a `*.meta.yaml` sidecar next to the
  source slice with `relation: sets` pointing at the canonical upstream CFR or
  USC slot.
- Do not leave promoted corpus files as `status: stub`.
- Do not hand-edit promoted policy outputs; improve the automatic system and rerun.
