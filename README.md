# Sharp Bounds for Truthful-in-Expectation Scheduling

Exact rational verification code for the paper by Yunpeng Li.

## Run all checks

Download `verify_scheduling.py` and run with Python 3.11 or newer:

```sh
python3 verify_scheduling.py --workers 2
```

Only the Python standard library is needed. No network access, external solver, or separate data download is used. Keep assertions enabled; do not use `-O`. A complete successful run reports `PASS` in `verification_report.json`. A previous full replay took about 10 minutes on the author's machine; runtime depends on the computer.

## Scope

The verifier checks the analytic two-machine certificate, the three-machine inequality over 75 computational support roots and 90,791 terminal boxes, and the piecewise rational two-machine approximation rule. All acceptance decisions use exact integer or rational arithmetic. The other 54 three-machine support orbits and the reductions to scheduling mechanisms are proved in the paper. The proofs for at least seven machines do not use these computations. This code is not a formal proof checker for the whole paper.

## Inspect the source

```sh
python3 verify_scheduling.py --extract-only readable_source
```

The standalone script embeds all 95 readable source and input files. Extraction performs no mathematical verification. See [README.txt](README.txt) for all options and [SOURCE_MAP.txt](SOURCE_MAP.txt) for provenance.

[VERIFICATION_REPORT.json](VERIFICATION_REPORT.json) and [VALIDATION.json](VALIDATION.json) record the existing replay and release tests. They are diagnostics, not inputs to the verifier. `SHA256SUMS` records file integrity, not proof correctness.
