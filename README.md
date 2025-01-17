[![name_matching](https://github.com/DeNederlandscheBank/name_matching/actions/workflows/python-app.yml/badge.svg?branch=main)](https://github.com/DeNederlandscheBank/name_matching/actions/workflows/python-app.yml)

# Name matching

Name matching is a Python package for the matching of company names

## Installation

The package can be installed via PiPy:

```bash
pip install name_matching
```

Alternatively you could install the package by downloading the repo, navigating to the folder and run the setup in pip locally

```bash
pip install .
```

## Usage

To see example usage of the package you can use the notebook folder. An example of the usage is also given below
```python
from name_matching.name_matcher import NameMatcher

# initialise the name matcher
matcher = NameMatcher(column='name', 
                      number_of_matches=3, 
                      legal_suffixes=True, 
                      common_words=False, 
                      top_n=50, 
                      verbose=True)

# adjust the distance metrics to use
matcher.set_distance_metrics(discounted_levenshtein=False,
                             bag=True,
                             typo=True,
                             refined_soundex=True)

# load the data to which the names should be matched
matcher.load_and_process_master_data(df_gleif, transform=True)

# perform the name matching on the data you want matched
matches = matcher.match_names(to_be_matched=unknown_counterparties, column_matching='name')


```

## Contributing
All contributions are welcome. For more substantial changes, please open an issue first to discuss what you would like to change.

## License
[MIT](https://choosealicense.com/licenses/mit/)
