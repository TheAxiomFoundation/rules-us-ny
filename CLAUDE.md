# cosilico-us-ny

**New York State tax and benefit statute encodings.**

All NY-specific .cosilico files belong here, NOT in cosilico-engine or cosilico-us.

## Structure

Files organized under `statute/` by law type and section:

```
cosilico-us-ny/
├── statute/               # All enacted statutes
│   ├── tax/              # NY Tax Law (Article 22 - Personal Income Tax)
│   │   ├── 601/          # Section 601 - Personal Income Tax Rates
│   │   │   ├── income_tax.cosilico
│   │   │   └── parameters.yaml
│   │   ├── 606/          # Section 606 - Tax Credits
│   │   │   ├── b/ny_eitc.cosilico          # NY EITC (30% of federal)
│   │   │   ├── c/empire_state_child_credit.cosilico
│   │   │   ├── household_credit.cosilico   # Section 606(b)
│   │   │   └── parameters.yaml
│   │   ├── 612/          # Section 612 - NY AGI Modifications
│   │   │   ├── ny_agi.cosilico
│   │   │   ├── ny_taxable_income.cosilico
│   │   │   └── parameters.yaml
│   │   └── 614/          # Section 614 - Standard Deduction
│   │       ├── standard_deduction.cosilico
│   │       └── parameters.yaml
│   │
│   └── nyc/              # NYC Administrative Code Title 11
│       ├── 1701/         # Section 11-1701 - NYC Income Tax
│       │   ├── income_tax.cosilico
│       │   └── parameters.yaml
│       ├── 1706/         # Section 11-1706 - NYC Credits
│       │   ├── credits.cosilico   # NYC EITC (5%) and School Tax Credit
│       │   └── parameters.yaml
│       ├── is_nyc_resident.cosilico
│       └── nyc_taxable_income.cosilico
│
└── tests/                # Validation test cases
    └── integration/
```

## Key NY Tax Provisions

### Personal Income Tax (Tax Law Section 601)
- 9 marginal brackets: 4%, 4.5%, 5.25%, 5.5%, 6%, 6.85%, 9.65%, 10.3%, 10.9%
- Brackets vary by filing status
- Supplemental tax applies for NY AGI > $107,650

### NY AGI Modifications (Tax Law Section 612)
- ADD: Interest from other states' municipal bonds
- SUBTRACT: Social Security benefits (NY does not tax)
- SUBTRACT: Up to $20,000 pension/annuity for age 59.5+
- SUBTRACT: Interest on US government obligations
- SUBTRACT: Up to $5,000 NY 529 plan contributions

### Standard Deduction (Tax Law Section 614)
- Single: $8,000
- Married Filing Jointly: $16,050
- Head of Household: $11,200
- Married Filing Separately: $7,500
- Dependent: $3,100

### NY EITC (Tax Law Section 606(d))
- 30% of federal EITC
- Refundable credit
- Reduced by household credit if claimed

### Empire State Child Credit (Tax Law Section 606(c))
- Greater of: $100 per child OR 33% of federal CTC
- Uses 2017 federal CTC rules ($1,000 base, age <17)
- Phase-out begins at $75,000 single / $110,000 joint
- Maximum $330 per qualifying child (33% of $1,000)

### Household Credit (Tax Law Section 606(b))
- Alternative to EITC for higher incomes
- $90 single, $180 joint, $130 HOH, $45 MFS
- Income limits: $28,000 single, $32,000 joint

### NYC Income Tax (Admin Code Section 11-1701)
- Separate city tax for NYC residents only
- 4 brackets: 3.078%, 3.762%, 3.819%, 3.876%
- Uses same taxable income base as NYS

### NYC EITC (Admin Code Section 11-1706)
- 5% of federal EITC (reduced from 10% in 2022)
- Refundable credit for NYC residents

### NYC School Tax Credit (Admin Code Section 11-1706)
- $63 single / $125 joint for incomes under $250,000
- Non-refundable credit for NYC residents

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
  ny_taxable_income: statute/tax/612/ny_taxable_income
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
- 2024 NY Tax Tables: https://www.tax.ny.gov/pit/file/tax-tables/2024.htm
