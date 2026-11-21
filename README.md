# How often the 547/727 prime race makes a large move

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24412163.svg)](https://doi.org/10.5281/zenodo.24412163)

This result is now maintained in [theta-host-split-inert-race](https://github.com/leecrossley/theta-host-split-inert-race/tree/main/results/theta-race-excursion-proportions). This repository is archived and keeps its releases and DOI.

In every interval of log starting heights of length at least 250,000, **more than 10% of starts give a gain above $`1.9735\log2`$ and more than 10% give a loss of that magnitude**. This holds for every such interval that starts at height one or above. Over increasingly long intervals the lower proportion exceeds 15% in each direction, uniformly in the starting height. The score width and the move are both two. [Theorem and proof](PROOF.md)

| Minimum log length | Guaranteed share for each sign |
|---:|---:|
| 20,000 | 1% |
| 50,000 | 6.25% |
| 100,000 | $`1/12`$ |
| 250,000 | 10% |
| Lower uniform log density | 15% |

The fractions weight each start $`y`$ by $`dy/y`$. For example, the 10% claim applies on every $`[H,H\exp(250000)]`$ with $`H\ge1`$. Every move compares the score at $`y`$ with the score at $`2y`$. [Score and theta trace](https://github.com/leecrossley/theta-race-short-shifts/blob/483c31f2df2132ed2165620ea55e20e969228bfb/RaceTrace.lean#L83) · [Prior work](PRIOR-WORK.md)

The calculation separates 1,281,601 frequencies built from 800 certified zero ordinates. This controls four moments on finite intervals without assuming that the zeros are linearly independent. A separate calculation counts the same near coincidences with binary searches. [Zero brackets](evidence/zero-brackets.tsv) · [Verification output](evidence/check.txt)

## Replay

In a Python 3.11+ environment with the pinned packages available, run

```sh
python -m pip install -r requirements.txt
python moments.py
python independent.py
python check_source.py
```

On x86-64 Linux with Git, curl, tar and zstd, `bash verify-release.sh` also checks the file hashes, the upstream theorem records and five local Lean deductions. With Lean 4.33.1 on PATH and a built Mathlib at commit `0df444a360eaa60ab8c11dca51a86af692955474`, run `bash verify-release.sh /path/to/mathlib4`. An optional second argument supplies the directory of the five upstream records. The explicit formula and averaging arguments are written mathematics. The four table rows are certified in Python with exact fractions. [Local Lean proof](ExcursionProportions.lean) · [File hashes](SHA256SUMS) · [Hardy-sign replay](https://github.com/leecrossley/theta-race-factor-400/releases/tag/v1.0.0)
