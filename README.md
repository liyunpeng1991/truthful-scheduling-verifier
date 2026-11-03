# Sharp Bounds for Truthful-in-Expectation Scheduling

This is the Python verifier for Yunpeng Li’s paper. It checks the finite certificates used for the two- and three-machine bounds.

## Run the verifier

Download `verify_scheduling.py` and run it with Python 3.11 or newer, with assertions enabled. It uses only the standard library and includes its certificate inputs.

```sh
python3 verify_scheduling.py --workers 2
```

A successful run writes `PASS` and the results of all three checks to `verification_run.json`. The worker count controls the three-machine computation. The supplied [verification report](VERIFICATION_REPORT.json) gives the exact results for comparison.

| Paper | What is checked |
| --- | --- |
| Section 6 | Rational enclosures for the analytic two-machine optimum, including the contraction, shape inequalities and boundary signs. |
| Section 7 | The two shared-clock examples and all 90,791 terminal boxes in the 75 computational support patterns. The paper proves the other 54 patterns directly. |
| Section 8 | The worst-case ratio of the piecewise rational two-machine rule, including a pair that attains the exact maximum. |

## Inspect the source or run one check

Extract the Python modules, certificate inputs and checksum manifest into a new or empty directory:

```sh
python3 verify_scheduling.py --extract-only readable_source
```

To run one group, pass `--only analytic`, `--only three`, or `--only rational`. A successful individual check reports `PARTIAL_PASS`. Use `--report FILE` for a different report path, or `--work-dir DIR` to retain the source and calculation outputs from a run. Run `--help` for all options.

The [source map](SOURCE_MAP.txt) identifies the modules for each computation. The [notation map](NOTATION_MAP.txt) relates their identifiers to the formulas in the paper. [SHA256SUMS](SHA256SUMS) lists the repository file hashes, and [PAYLOAD_SHA256.txt](PAYLOAD_SHA256.txt) gives the hash of the ZIP embedded in the script.
