Energy measurement reproduction guide

Follow these steps to reproduce the experiments, collect energy measurements, and run the analysis.

1) Generate the test JSON

- Open and run `test.ipynb` (Jupyter). The notebook creates a large JSON file used for the measurements.
- By default the notebook generates a 5 GB file. To change the size, edit the numeric size (MB) value `5000` in the notebook. Example: set it to `1000` to create a 1 GB file.

2) Run the energy measurement

- Use the PowerShell script `run_energy_measurement.ps1` to run the measurement harness. The script reads the JSON and produces a CSV of results.
- By default the script runs 30 iterations. Override with the `-Iterations` parameter.

Example (run 50 iterations):

```powershell
.\run_energy_measurement.ps1 -Iterations 50
```

Outputs:
- `*.json` — generated test data (from step 1)
- `*.csv` — measurement results (one CSV per run)

3) Run the analysis

- Open and run the analysis notebook `analysis/energy_json_vs_orjson.ipynb`. It consumes the CSV(s) and produces the figures and summary tables used in the paper.

Notes and tips
- If you need smaller/faster test runs while iterating, reduce the JSON size and `-Iterations` so experiments finish quickly.
- Keep generated large files (JSON) on a drive with sufficient free space.