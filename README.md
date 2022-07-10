# OpenPGx [![build](https://github.com/monigenomi/openpgx/workflows/CI/badge.svg)](https://github.com/monigenomi/openpgx/actions) 

OpenPGx is software with useful pharmacogenomics utilities.

It now implements to convert human's genotype to phenotype and annotate with gene-drug recommendations (for all drugs having recommendations in CPIC, DPWG, or FDA pharmacogenomics databases)

## Usage

```sh
$ openpgx recommendations --genotype <file> [--output <file>]
  
  Computes pharmacogenomics recommendations from local database.
    
  Options:
    -g, --genotype JSON file with genotypes to filter recommendations
    -o, --output   Output file location [default: recommendations.json] 
  
  An example genotype.json (under path passed using `--genotype` or `-g` flag):
  
    {
      "SLCO1B1", "*1A/*1B",
      "CYP2D6": "*2≥3/*1≥3",
      "HLA-A*31:01": "positive",
      "HLA-B*15:02": "negative",
      "DPYD": "c.601A>C/c.2194G>A (*6)",
      "G6PD": "B (wildtype)"
    }
  
Thank you for using OpenPGx! We will appreciate Your feedback and contributions at:
https://github.com/monigenomi/openpgx
```

## Development

You can setup development environment and run tests with following commands:

```sh
python3 -m venv venv
source venv/bin/activate
pip install -e '.[dev]'
pytest -vv
```

If you wish to compute recommendations from raw databases, you can use `openpgx update` command:

```sh
$ openpgx update
  
  Re-computes recommendations database for CPIC, DPWG, and FDA.
  
  You can use this command for example to test and implement new kinds of recommendation.
  
  Options:
    --cpic   Link or path from which to fetch CPIC recommendations, default:
       https://github.com/cpicpgx/cpic-data/releases/download/v1.10/cpic_db_dump-v1.10_inserts.sql.gz
    --dpwg   Link or path from which to fetch DPWG recommendations, default:
       https://api.pharmgkb.org/v1/download/file/data/dosingGuidelines.json.zip
    --fda    Link or path from which to fetch FDA recommendations, default:
       https://raw.githubusercontent.com/PharmGKB/fda-biomarker/master/fda_pgx_associations_table.json
```

## Development

Some tips:

- Please add tests for each change you make
- Recommendations database generation is best done by debugging "openpgx update" command
- It's best to use `python -m openpgx` during development as it handled module loading properly

## License

EUPL v1.2
