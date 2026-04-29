# rules-us-ny

New York RuleSpec encodings and source registry metadata.

## Contents

- `statutes/`: New York statute RuleSpec YAML, with tests beside each encoding as `.test.yaml`.
- `regulations/`: New York regulation RuleSpec YAML, with tests beside each encoding as `.test.yaml`.
- `policies/`: New York policy RuleSpec YAML, with tests beside each encoding as `.test.yaml`.
- `sources/`: source registry or manifest metadata when needed.
- `.github/workflows/repository-checks.yml`: wrapper around the shared RuleSpec validation workflow.

## Conventions

Use RuleSpec YAML for encoded rules. Do not add legacy `statute/`,
`parameters.yaml`, `tests.yaml`, `tests/*.yaml`, or `.rac` artifacts.

Federal materials belong in `rules-us`. New York-administered state and city materials belong here.
