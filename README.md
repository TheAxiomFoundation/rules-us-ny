# cosilico-us-ny

New York State tax and benefit statute encodings for the Cosilico platform.

## Overview

This repository contains machine-readable encodings of New York State tax law and benefit programs. It builds on federal calculations from `cosilico-us`.

## Coverage

### State Taxes (NY Tax Law)
- **Personal Income Tax (§ 601)** - 9-bracket progressive tax (4% to 10.9%)
- **Standard Deduction (§ 614)** - Filing status-based deductions
- **NY EITC (§ 606(d))** - 30% of federal earned income credit
- **Empire State Child Credit (§ 606(c))** - Child tax credit for NY residents

### NYC Taxes (Administrative Code Title 11)
- **NYC Income Tax (§ 11-1701)** - 4-bracket city tax (3.078% to 3.876%)
- **NYC EITC (§ 11-1706)** - 5% of federal earned income credit
- **School Tax Credit** - $63/$125 for qualifying NYC residents

## Usage

```python
from cosilico import load_repo

# Load NY statutes
ny = load_repo("cosilico-us-ny")

# Calculate NY income tax
situation = {
    "tax_unit": {
        "ny_agi": 75000,
        "filing_status": "SINGLE"
    }
}

result = ny.calculate("ny_income_tax", situation, period="2024")
```

## Structure

```
statute/
├── tax/                  # NY Tax Law
│   ├── 601/             # Income tax rates
│   ├── 606/             # Credits (EITC, ESCC)
│   └── 614/             # Standard deduction
│
└── nyc/                  # NYC Administrative Code
    ├── 1701/            # NYC income tax
    └── 1706/            # NYC credits
```

## Development

### Prerequisites
- Python 3.11+
- cosilico-engine

### Issue Tracking
```bash
bd ready                 # Show available work
bd create "Title" -t task -p 2
bd update <id> --status in_progress
bd close <id>
```

## License

MIT
