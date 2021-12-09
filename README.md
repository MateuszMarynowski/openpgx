# OpenPGx [![build](https://github.com/monigenomi/openpgx/workflows/CI/badge.svg)](https://github.com/monigenomi/openpgx/actions) 

OpenPGx is software to convert human's genotype to phenotype and annotate with gene-drug recommendations (for all drugs having recommendations in CPIC, DPWG, or FDA pharmacogenomics databases)

## Development

```sh
python3 -m venv venv
source venv/bin/activate
pip install -e '.[dev]'
pytest
```

## License

EUPL v1.2
