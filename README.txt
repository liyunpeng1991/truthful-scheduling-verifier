EXACT VERIFIER FOR SHARP BOUNDS FOR TRUTHFUL-IN-EXPECTATION SCHEDULING
Prepared 2 November 2026

QUICK START
Download verify_scheduling.py. Use Python 3.11 or newer, with assertions enabled.
No third-party packages, network access, solver, Mathematica, or separate data
files are needed. In a terminal in the download folder, run:

    python3 verify_scheduling.py --workers 2

The default run freshly checks all three computational premises and writes
verification_report.json in the current folder. Acceptance requires status PASS
and all three checks completed. The included VERIFICATION_REPORT.json records
our completed replay; it is not read by the verifier.

--workers 1 also runs the complete check and uses one worker for the
three-machine calculation. Two workers took about 10 minutes 16 seconds in our
full local replay (Python 3.12.14); runtime depends on the computer. The program
prints progress. It processes terminal boxes in bounded batches. Do not run
with -O or PYTHONOPTIMIZE: assertions are part of the acceptance checks.

WHAT IS CHECKED
1. Analytic two-machine curve: exact rational residual, denominator, Jacobian,
   contraction, shape-cover and endpoint-sign bounds, including the more precise
   constants displayed in the paper. All 19 shape intervals are covered.
2. Three-machine normalized inequality: complete closed subdivision trees for
   75 computational support roots, 181,507 records and 90,791 terminal boxes;
   fresh rational probability integrals and repaired dual bounds at every leaf.
   The other 54 support orbits have mathematical proofs in the paper.
3. Piecewise rational two-machine rule: exact maximization over 44,118 polygons
   and 178,506 candidate extrema, establishing the factor 752998007/500000000.

All acceptance comparisons use exact integers or fractions; square roots use
outward rational enclosures computed with integer square roots. The code checks
finite premises. The reductions to mechanisms, incentive arguments and lower
bounds are mathematical arguments in the paper. This is not a formal proof
assistant for the whole manuscript.

READ THE SOURCE
The single file is about 7.1 MiB because it embeds a compressed archive of the
readable Python modules AND the finite mathematical inputs. Extract them with:

    python3 verify_scheduling.py --extract-only readable_source

Use a new or empty destination. Extraction performs no mathematical checks.
The extracted source/data occupies about 76 MB. See SOURCE_MAP.txt for the module
roles and provenance. The archive contains no stored success receipts or
terminal upper bounds. Every acceptance bound is recomputed. Hashes check file
integrity; they are not the mathematical justification.

For an individual check:

    python3 verify_scheduling.py --only analytic
    python3 verify_scheduling.py --only rational
    python3 verify_scheduling.py --only three --workers 2

An individual successful check reports PARTIAL_PASS, never full PASS. An
interrupted or failed run is not acceptance. Use --report FILE to choose the
report path; the default report is overwritten on a new run. Use --work-dir DIR
with a new directory to retain the extracted modules and generated diagnostics.
Without it, the program uses and removes a temporary extraction directory.
Run --help for all options.

VALIDATION OF THIS RELEASE
The full fresh replay of the embedded modules passed all three checks. The
standalone launcher was separately tested for extraction, help and individual
checks. Negative tests rejected an incomplete cover, duplicate child, invalid
terminal bound, disabled assertions and a damaged payload. See VALIDATION.json
for the precise test scope and hashes, and VERIFICATION_REPORT.json for exact
results. These reports are diagnostic artifacts, not verifier inputs.

PYTHON OR MATHEMATICA?
Python is the primary release: the current exact replay has been executed, and
readers need only the standard library. Mathematica is useful as an optional
companion for compact symbolic calculations and independently checking algebra.
The project's earlier Mathematica prototype was not executed in a Wolfram
kernel; it should not be presented as an independently validated verifier.
The language itself does not confer rigor: exact arithmetic, complete coverage
and explicit acceptance conditions are what matter.
