# Canadian Federal Ridings

A single JSON file listing all **343 federal electoral districts (ridings)** of Canada, with province codes, official riding IDs, and names in both English and French.

The list reflects the **2023 Representation Order**, in effect since the 2025 federal election, including the 19 riding renames enacted by *An Act to change the names of certain electoral districts, 2026* (Part 2 of Bill C-25, the *Strong and Free Elections Act*).

## Data

Everything lives in [`ridings.json`](ridings.json) — an array of 343 objects:

```json
{
  "id": 10006,
  "prov": "NL",
  "name_en": "St. John's East",
  "name_fr": "St. John's-Est"
}
```

| Field     | Description                                                                                             |
| --------- | ------------------------------------------------------------------------------------------------------- |
| `id`      | Elections Canada electoral district number. The first two digits encode the province or territory (e.g. `10` = NL, `35` = ON), the last three the riding within it. |
| `prov`    | Two-letter postal abbreviation of the province or territory (`AB`, `BC`, `MB`, `NB`, `NL`, `NS`, `NT`, `NU`, `ON`, `PE`, `QC`, `SK`, `YT`). |
| `name_en` | Official riding name in English.                                                                         |
| `name_fr` | Official riding name in French. Identical to `name_en` where no French form exists.                      |

### Ridings per province and territory

| Province / Territory | Code | Ridings |
| -------------------- | ---- | ------: |
| Ontario              | ON   |     122 |
| Quebec               | QC   |      78 |
| British Columbia     | BC   |      43 |
| Alberta              | AB   |      37 |
| Manitoba             | MB   |      14 |
| Saskatchewan         | SK   |      14 |
| Nova Scotia          | NS   |      11 |
| New Brunswick        | NB   |      10 |
| Newfoundland and Labrador | NL |      7 |
| Prince Edward Island | PE   |       4 |
| Northwest Territories | NT  |       1 |
| Nunavut              | NU   |       1 |
| Yukon                | YT   |       1 |
| **Total**            |      | **343** |

## Usage

```js
// JavaScript
const ridings = require("./ridings.json");
const ontario = ridings.filter((r) => r.prov === "ON");
```

```python
# Python
import json

with open("ridings.json") as f:
    ridings = json.load(f)

by_id = {r["id"]: r for r in ridings}
print(by_id[10006]["name_fr"])  # St. John's-Est
```

## License

Riding names and district numbers are public information published by [Elections Canada](https://www.elections.ca/).
