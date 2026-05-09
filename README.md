# rules-us-ny

New York RuleSpec encodings.

## Contents

- `statutes/`: New York statute RuleSpec YAML, with tests beside each encoding as `.test.yaml`.
- `regulations/`: New York regulation RuleSpec YAML, with tests beside each encoding as `.test.yaml`.
- `policies/`: New York policy RuleSpec YAML, with tests beside each encoding as `.test.yaml`.
- `.github/workflows/repository-checks.yml`: wrapper around the shared RuleSpec validation workflow.

## Conventions

Use RuleSpec YAML for encoded rules. Do not add source text, source registry
sidecars, generated source payloads, singular rule roots, separate
parameter/test fixture files, or generated formula artifacts.

Federal materials belong in `rules-us`. New York-administered state and city materials belong here.
