# Harness

## Setup

The settings of Claude Code for all repos of treporting are kept in `~/git/treporting/.claude/`,
one level above the repos.

## Process

treporting is developed following the process of the domain *industrial* (see
[standards.md](standards.md)):

- **IEC 61508** is the reference for the life cycle. treporting is no safety function but a tool,
  so no SIL applies: IEC 61508 is the process model, and REG-02 (tool class T2) the requirement
  on the tool.
- **safety analysis**: the hazard and risk analysis after IEC 61508-1, 7.4, in
  [safety/hazard-and-risk-analysis.md](safety/hazard-and-risk-analysis.md).
- **security**: IEC 62443-4-1 for the secure development, IEC 62443-3-2 for the analysis of the
  threats (THR, #22).

### Levels

| Level | Here | IEC 61508 |
|---|---|---|
| r1 | user needs (UN), regulatory requirements (REG) | -1, 7.2 concept, 7.3 overall scope; 7.4 hazard and risk analysis (HAZ) |
| r2 | system requirements (SYS) | -1, 7.5 overall safety requirements; 7.10 E/E/PE system safety requirements |
| r3 | system architecture (ARC) | -2, 7.4 E/E/PE system design and architecture |
| r4 | the system requirements allocated to the subsystems - derived directly from r2 by the allocation in the system architecture, with no ids of their own | -1, 7.6 overall safety requirements allocation |
| r5 | software requirements (SR) per subsystem | -3, 7.2 software safety requirements specification |

### Maturity of our own data

The data of treporting itself (the reference edgedb, #9) is measured by the chain of
IEC 61508-3:

| Order | Object | IEC 61508-3 | Group |
|---|---|---|---|
| 1 | system requirement | -2, 7.2 | RG-SYS-R |
| 2 | system architecture | -2, 7.4 | RG-SYS-R |
| 3 | software requirement | 7.2 | RG-SW-R |
| 4 | software architecture | 7.4.3 | RG-SW-R |
| 5 | software system design | 7.4.5 | RG-SW-R |
| 6 | module design | 7.4.5 | RG-SW-R |
| 7 | source code, one step per coverage level | 7.4.6 | RG-SC |
| 8 | object code, one step per coverage level | - | RG-OC |
| 9 | test case, test result of the module test | 7.4.7 | RG-SW-TC, RG-SW-TR |
| 10 | test case, test result of the module integration test | 7.4.8 | RG-SW-TC, RG-SW-TR |
| 11 | test case, test result of the integration of software and hardware | 7.5 | RG-SW-TC, RG-SW-TR |
| 12 | test case, test result of the software validation | 7.7 | RG-SYS-TC, RG-SYS-TR |

With one coverage level each, the chain has 16 steps.

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
| PROC-08 | Every release has an SBOM, and the licences of its components are checked against Apache-2.0 (REG-15, REG-18). |
| PROC-09 | A reported vulnerability is assessed and fixed without delay; one that is actively exploited is notified within 24 hours (REG-15, REG-16). |
| PROC-10 | Every release gets security fixes over the support period it states (REG-17). |

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
6. create the SBOM and check the licences of the components (PROC-08)
7. provide feedback
8. create a signed tag as approval (PROC-06)
9. write the data of the release or library into a separate edgedb, kept as reference
   data - the real data of treporting itself, used instead of synthetic data to show that
   it works in practice (PROC-07)
