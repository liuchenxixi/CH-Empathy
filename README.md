# CH-Empathy v1

CH-Empathy v1 is a weak-empathy resource built from an IRI seed survey and a CGSS2023-compatible social-variable schema. This release package provides public documentation, metadata, reconstruction scripts, benchmark scripts, and aggregate validation results for reproducibility review.

This GitHub copy is a temporary public mirror prepared before the formal Dataverse release. After the Dataverse record is published, the archived DOI should be used as the primary citation and access point.

## Repository contents

- Metadata for semantic variables, recoding rules, one-hot feature names, and variable descriptions.
- Scripts for reconstructing CGSS2023-derived feature tables from an authorized local CGSS2023 copy.
- Teacher-model, benchmark, TabNet, and construct-validity scripts.
- Aggregate benchmark and validation result tables used by the accompanying paper.
- Split configuration for reproducing the reported benchmark protocol.
- Citation, license, datasheet, and data-access documentation.

## Data availability

This public package does **not** redistribute:

- CGSS2023 raw data;
- CGSS row-level derived tables;
- raw seed-survey records.

CGSS2023 data must be obtained from the official CGSS provider under its original access and redistribution terms. Users with authorized CGSS2023 access can run the reconstruction scripts locally to reproduce the aligned feature tables.

Seed-survey row-level records are not included because they may contain sensitive demographic, socioeconomic, and psychological variables. See `data_access_terms.md` for the access and acceptable-use statement.

## Basic reproduction workflow

1. Download and unzip `CH-Empathy-v1.zip`.
2. Obtain authorized CGSS2023 data from the official provider.
3. Edit `examples/example_config.yaml` with the local CGSS2023 data path and output directory.
4. Reconstruct the CGSS2023-compatible feature table:

   ```bash
   python scripts/reconstruct_cgss2023.py --config examples/example_config.yaml
   ```

5. Build the internal three-class weak-empathy labels:

   ```bash
   python scripts/build_mi_internal_3class.py --config examples/example_config.yaml
   ```

6. Run benchmark and TabNet evaluation scripts as needed:

   ```bash
   python scripts/evaluate_benchmark.py --config examples/example_config.yaml
   python scripts/train_tabnet.py --config examples/example_config.yaml
   ```

The included `results/` directory contains aggregate tables from the prepared release. Reproduction of row-level feature tables requires authorized access to CGSS2023 and local reconstruction.

## Citation

If you use this resource, please cite the formal Dataverse DOI once it becomes available.

Temporary citation before DOI registration:

```text
CH-Empathy v1: A Weak-Empathy Resource with CGSS2023-Compatible Social Variables.
Version 1.0.0. GitHub temporary public mirror, 2026.
```

After Dataverse publication, replace the temporary citation with:

```text
[Author Name]. CH-Empathy v1: A Weak-Empathy Resource with CGSS2023-Compatible Social Variables.
Version 1.0.0. Dataverse. DOI: [TO_BE_ADDED].
```

## License

The code and scripts are released under the MIT License. Documentation, metadata, and aggregate result tables are released under CC BY 4.0 unless otherwise stated.

This license does not apply to CGSS2023 raw data or any restricted third-party data. Users are responsible for complying with the original CGSS access and redistribution terms.

## Contact

For questions about this resource, please contact:

```text
Chenxi Liu
Nanjing Normal University
13782380982@163.com
```
