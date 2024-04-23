# PyPI semantic versions

This repo analyzes PyPI package versions and determines:
- How many packages use semantic versions? (using https://pypi.org/project/semantic-version/)
- Of these, how many use 0.x, 1.x, 2.x and up major versions?


## Running

```bash
pip install -r requirements.txt
jupyter notebook pypi_analysis.ipynb
```


## Data source

Data was obtained following this guide: https://warehouse.pypa.io/api-reference/bigquery-datasets.html

The BigQuery query I used to generate the CSV was this:

```sql
SELECT
  name,
  MAX(version) AS latest_version
FROM
  `bigquery-public-data.pypi.distribution_metadata`
GROUP BY
  name
```

I generated the CSV on April 20, 2024.
