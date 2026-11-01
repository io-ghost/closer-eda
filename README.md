# closer-eda (working name)

> **There is no result here yet.** No benchmark has been run, no design has been
> measured, and nothing in this repository should be quoted as evidence of
> performance.

**Repository state:** this README describes the project. The harness itself
(parsers, ECO strategy library, structural audit, append-only experiment store,
loop driver, report generator, ORFS planner, and its unit test suite) is
committed in the local development tree and lands here with the first code push.
Until that push, this repository contains only this file.

## The question

Most of PPA optimisation is automated in modern flows. The last stretch —
post-route timing, DRC and congestion cleanup — is still expert manual work, and
it is where tapeouts slip. This project tests one narrowly scoped question:

> Given a routed netlist that fails timing or DRC, which **function-preserving**
> edit sequence closes the most violation per unit of compute — and can the
> choice be learned cheaply enough to beat a *tuned* baseline, reproducibly?

## What will be in the tree

| Piece | State |
|---|---|
| OpenSTA / ORFS `metrics.json` / DRC report parsers | implemented, unit-tested against fixtures |
| By-construction-safe ECO strategy library | implemented (8 strategies, parameterised) |
| Structural netlist audit (stand-in for formal equivalence) | implemented, explicitly **not** LEC |
| Append-only experiment store (SQLite) | implemented, enforced by triggers |
| Proxy/truth two-tier loop driver | implemented, tested with fake runners |
| Static HTML report | implemented (synthetic demo only) |
| ORFS sweep planner (pure, prints commands) | implemented |
| Real ORFS execution | **not wired up** — needs an ORFS checkout |
| Any measurement of any design | **none** |
| Commercial-tool adapters | **none** (later, on a customer's licenses) |

## Honesty rules this project follows

1. No claim without a recorded run id, a seed, a tool version and a command.
2. The structural audit is a stand-in for formal equivalence, never called LEC.
3. Parsers that cannot find a required metric raise instead of returning "clean".
4. The experiment store is append-only; corrections are new rows.
5. Synthetic data is always banner-labelled.

These rules exist because this community has already been burned by
irreproducible placement claims — and earned skepticism is the default we are
walking into.

## Links

- Project page: https://io-ghost.github.io/
- Methodology is written before any run and will be published with the first result.

## License

MIT. OpenROAD/ORFS themselves are BSD-3-Clause. No PDK content is included or
redistributed here.
