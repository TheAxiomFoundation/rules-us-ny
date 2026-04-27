# rules-us-ny

New York RuleSpec source registry and policy metadata.

## Contents

- `sources/slices/otda/snap/current-effective/`: SNAP source slices and sidecar metadata.
- `statute/tax/*/parameters.yaml`: New York tax parameter tables retained as structured reference data.
- `statute/nyc/*/parameters.yaml`: New York City tax parameter tables retained as structured reference data.
- `.github/workflows/ci.yml`: repository guard for legacy executable formula payloads.

## Conventions

Use RuleSpec YAML for new encoded rules. Keep source text in `sources/slices/` with matching `.meta.yaml` files that record provenance and relations. Large XML or source payloads belong in object storage, with only registry or manifest metadata in Git.

Federal materials belong in `rules-us`. New York-administered state and city materials belong here.
