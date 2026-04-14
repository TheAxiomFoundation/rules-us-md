# rac-us-md

Maryland jurisdiction-specific RAC source and encoding corpus.

This repo is for Maryland-administered policy layers. Federal program cores stay
in `rac-us`; Maryland overlays, manuals, guidance, and state-specific encodings
live here.

## Current scope

- Maryland SNAP source slices for delegated SNAP state options
- jurisdiction-local source corpus for Maryland SNAP overlays

## Layout

```text
rac-us-md/
├── sources/
│   └── slices/
│       └── dhs/
│           └── snap/
│               └── current-effective/
├── scripts/
│   ├── check_no_promoted_stubs.py
│   └── validate_repo.py
└── CLAUDE.md
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

- Repo boundaries follow jurisdictions.
- Keep Maryland-administered overlays in `rac-us-md`, even when they sit on top
  of a federal program like SNAP.
- Keep exact local excerpts in `sources/slices/`.
- When a Maryland source sets a value inside a federally delegated slot, add a
  `*.meta.yaml` sidecar next to the source slice with `relation: sets` pointing
  to the canonical upstream CFR or USC target.
- Do not hand-edit promoted policy outputs; use AutoRAC plus benchmarked repair
  loops.
