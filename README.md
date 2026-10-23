# doc

User needs, requirements, architecture and the way of working of
[treporting](https://github.com/treporting) - a tool that reports traceability and maturity
from the systems a project keeps its work in, and only reads them.

## Files

| File | What it holds | Ids |
|---|---|---|
| [harness.md](harness.md) | how we work: the process we follow (IEC 61508), our levels, the rules of our work, the loops for every change and every release | `PROC-nn` |
| [definitions.md](definitions.md) | the terms: system, item, content, work product, release, library, baseline, traceability | - |
| [standards.md](standards.md) | the process, safety and security standards per domain | - |
| [requirements/user-needs.md](requirements/user-needs.md) | what each role needs, without a solution (r1) | `UN-<role>-nn` |
| [requirements/regulatory-requirements.md](requirements/regulatory-requirements.md) | what standards and laws ask | `REG-nn` |
| [requirements/system-requirements.md](requirements/system-requirements.md) | what the system has to do, seen as one box (r2); each section is a feature | `SYS-nn` |
| [architecture/system-architecture.md](architecture/system-architecture.md) | the subsystems, their interfaces, the rationale and the decisions, and which subsystem realizes which requirement (r3) | `ARC-nn` |
| [safety/hazard-and-risk-analysis.md](safety/hazard-and-risk-analysis.md) | the hazards treporting can cause | `HAZ-nn` |

The software requirements (r5, `SR-<subsystem>-nn`) live in the repo of their subsystem, next to
the code that realizes them.

## How the ids hang together

```
UN  (needs of a role)   ─┐
REG (standards, laws)   ─┼─→  SYS  ─→  ARC  ─→  SR  ─→  code, tests
HAZ (hazards)           ─┘     ↑
THR (threats) ─────────────────┤  a threat to the product leads to SYS
                └──────────────→  PROC  a threat to our work leads to a rule of the harness
```

The threats (`THR-nn`) are being worked out in #22.

Every need and every regulatory requirement that treporting realizes has at least one system
requirement; every system requirement names where it comes from and is allocated to the
subsystems that realize it.

## Way of working

Every change has a ticket in the [project treporting](https://github.com/orgs/treporting/projects/3)
and a branch of its own, and reaches `main` only through a pull request - see the rules in
[harness.md](harness.md).

## Licence

[Apache-2.0](LICENSE).
