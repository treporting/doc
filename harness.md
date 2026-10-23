# Harness

## Setup

The settings of Claude Code for all repos of treporting are kept in `~/git/treporting/.claude/`,
one level above the repos.

## Rules

The ids are `PROC-nn`. They are kept apart from the ids of the requirements, so that keeping
to the process does not count into the maturity of the product.

| Id | Rule |
|---|---|
| PROC-01 | The language for tickets, code, code comments and documentation is English only. |
| PROC-02 | Every change has a ticket in the org project treporting and a branch `<ticket number>-<slug>`. |
| PROC-03 | A change reaches `main` only through a pull request; `main` is protected. |
| PROC-04 | A pull request passes the full gate before it is merged to `main`. |
| PROC-05 | A requirement is merged before any code names it in `@implements`. |
| PROC-06 | A baseline is a signed tag: in doc it is a release, in any other repo a library. |
| PROC-07 | Every release and every library writes its data into the reference edgedb. |

## Loop for every code change

1. compile
2. run linter
3. run unit-testing in local
4. update documentation (swagger, *.md)
5. gate checks - the quick gate before a commit, the full gate before a merge to main (PROC-04)
6. commit, pull request, merge (PROC-03)
7. provide feedback

## Loop for every release or library

1. compile
2. run linter
3. run unit-testing in local
4. run spec-testing on test environment
5. report on
   - test coverage
   - structural debt
   - requirements
6. provide feedback
7. create a signed tag as approval (PROC-06)
8. write the data of the release or library into a separate edgedb, kept as reference
   data - the real data of treporting itself, used instead of synthetic data to show that
   it works in practice (PROC-07)

## Optimization

- Token-efficient error outputs
    - When a test or linter fails, filter the output before passing it back to the agent. Instead of 500 lines of stack trace, the last 20 lines along with the specific error code and file path are usually enough.
- Embed an architecture linter
    - Extend the linting step with a tool to enforce layer and package boundaries (e.g., go-arch-lint for Go or dependency-cruiser / ESLint boundaries for React/TS). This automatically prevents structural debt.
