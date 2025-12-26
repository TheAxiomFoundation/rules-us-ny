# cosilico-us-ny

**New York State tax and benefit statute encodings.**

All NY-specific .cosilico files belong here, NOT in cosilico-engine or cosilico-us.

## Structure

Files organized under `statute/` by law type and section:

```
cosilico-us-ny/
├── statute/               # All enacted statutes
│   ├── tax/              # NY Tax Law
│   │   ├── 601/          # § 601 - Personal Income Tax Rates
│   │   │   ├── income_tax.cosilico
│   │   │   └── parameters.yaml
│   │   ├── 606/          # § 606 - Tax Credits
│   │   │   ├── b/ny_eitc.cosilico          # NY EITC (30% of federal)
│   │   │   ├── c/empire_state_child_credit.cosilico
│   │   │   └── parameters.yaml
│   │   └── 614/          # § 614 - Standard Deduction
│   │       ├── standard_deduction.cosilico
│   │       └── parameters.yaml
│   │
│   └── nyc/              # NYC Administrative Code Title 11
│       ├── 1701/         # NYC Income Tax
│       │   ├── income_tax.cosilico
│       │   └── parameters.yaml
│       └── 1706/         # NYC EITC and School Tax Credit
│           └── credits.cosilico
│
└── tests/                # Validation test cases
    └── integration/
```

## Key NY Tax Provisions

### Personal Income Tax (Tax Law § 601)
- 9 marginal brackets: 4%, 4.5%, 5.25%, 5.5%, 6%, 6.85%, 9.65%, 10.3%, 10.9%
- Brackets vary by filing status
- Supplemental tax applies for NY AGI > $107,650

### Standard Deduction (Tax Law § 614)
- Single: $8,000
- Married Filing Jointly: $16,050
- Head of Household: $11,200
- Married Filing Separately: $7,500
- Dependent: $3,100

### NY EITC (Tax Law § 606(d))
- 30% of federal EITC
- Refundable credit

### Empire State Child Credit (Tax Law § 606(c))
- $100 per child OR 33% of federal CTC, whichever is greater
- Refundable for qualifying families
- Uses 2017 federal CTC rules for calculation

### NYC Income Tax (Admin Code § 11-1701)
- Separate city tax for NYC residents
- 4 brackets: 3.078%, 3.762%, 3.819%, 3.876%
- NYC EITC: 5% of federal EITC

## References in .cosilico files

Cross-repo references use full paths:
```
references {
  # Federal inputs from cosilico-us
  federal_eitc: cosilico-us:statute/26/32/a/1/earned_income_credit
  federal_agi: cosilico-us:statute/26/62/a/adjusted_gross_income
  federal_ctc: cosilico-us:statute/26/24/child_tax_credit

  # Intra-repo references
  ny_agi: statute/tax/612/ny_agi
}
```

## File Types

- `.cosilico` - Executable formulas (compile to Python/JS/WASM)
- `parameters.yaml` - Time-varying values (rates, thresholds, brackets)
- `tests.yaml` - Validation test cases

## Related Repos

- **cosilico-us** - Federal tax/benefit statute encodings (inputs to state calculations)
- **cosilico-engine** - DSL compiler and runtime
- **cosilico-validators** - Validation against external calculators

## Official Sources

- NY Tax Law: https://www.nysenate.gov/legislation/laws/TAX
- NY Tax Department: https://www.tax.ny.gov
- NYC Administrative Code: https://codelibrary.amlegal.com/codes/newyorkcity
