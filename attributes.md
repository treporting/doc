# Attributes of the model

Every attribute of the model, type by type: what it means, where it comes from, whether it has an
inherited (`I`) or a mapped (`M`) variant, how it is carried down the trace, and which system
requirements use it. The names are those of the gel schema of the model and of the YAML
([formats.md](formats.md)). The terms are those of
[definitions.md](definitions.md).

Where it comes from:

- **author** - written in the source, in our YAML by the author
- **context** - where the object lies, given by the extractor
- **derived** - made by the import, never written in the source

The prefixes: `I` inherited - carried down the trace; `M` mapped - translated or adapted to the
model by the configuration of the customer. The original is always kept beside them.

## All types

### created_at, created_by, modified_at, modified_by

| | |
|---|---|
| Meaning | when and by whom an object was created in its source, and when and by whom it was last modified there |
| Value | a time with its zone; the name of a person as the source gives it |
| Comes from | the source, as it records it - DOORS, for instance, keeps *Created On*, *Created By*, *Last Modified On*, *Last Modified By*; for a file in GIT the commit gives them |
| Note | not the time of the import: that is in the import record. The names are personal data, kept only for the purposes set (UN-ALL-04, SYS-44) |
| Used by | REG-10, data attributable to whom it comes from; SYS-16, what changed between two baselines |

## Requirement

### platform_launch

| | |
|---|---|
| Meaning | the platforms a requirement holds for, and per platform the launches it is planned for |
| Value | one line per platform, its launches after `=` separated by commas, each launch its number and its type: `platform-1 = 1_type1, 2_type1, 2_type2`, next line `platform-2 = 1_type1, 2_type1, 2_type2`; spaces around `=` and after a comma are allowed |
| Comes from | author, on r1 |
| Variants | `iplatform_launch` inherited, `mplatform_launch` mapped |
| Carried down | yes. A requirement with several parents carries the **union** of their platforms and launches - it holds wherever any of them holds (unlike the safety class, where the highest is carried) |
| Used by | SYS-09 filter over the whole trace; SYS-11 carrying down. The selection of a release offers the launches that release has |
| Version | a new version of an object where its launches change, not with every release |
| Open | the value `all`: resolved into the platforms by the converter, by the configuration of the customer |

### category

| | |
|---|---|
| Meaning | the level of the architectural breakdown an object belongs to |
| Value | `system`, `subsystem`, `component` or `unit` |
| Comes from | author |
| Note | a code function or method is no category - it is where an annotation stands |

### object_id and module_prefix

| | |
|---|---|
| Meaning | `object_id` is the number of an object within its module - a document, kept as folder and name; it is unique only within that module. `module_prefix` is an abbreviation that makes the module unique within its RProject or LProject |
| Example | the LProjects converter-edgedb, reporter-edgedb and viewer-edgedb each hold a document *SoftwareRequirements* with the prefix `SR`; its requirements are numbered within it. A link to one of them is written with the prefix: `target_ids = SR_12` |
| Comes from | context (the module), the author (the number) |

### changes

| | |
|---|---|
| Meaning | the names of the attributes that changed against the previous version of the object |
| Use | to show the difference between two versions efficiently - SYS-16 |
| Comes from | derived, by comparing with the previous version |

### verification_method

| | |
|---|---|
| Meaning | how a requirement is verified, after ISO/IEC/IEEE 29148 |
| Value | `inspection`, `analysis`, `demonstration` or `test` |
| Where | on the requirements of the software design (r7) |
| Comes from | author |
| Variants | `mverification_method` mapped - the converter maps the values of a customer to those of 29148: *review* to `inspection`, *design* to `analysis`. A customer may keep it in an attribute called coverage, which is a different thing here: the converter has to take care |

### coverage

| | |
|---|---|
| Meaning | how far the code is covered by tests: the code coverage level, such as `function` or `statement` coverage |
| Comes from | derived, from the coverage reports of the test runs - never written by an author |
| Used by | the chain of maturity: one step per code coverage level of source and object code |

### signal_ids, parameter_ids, issue_ids

| | |
|---|---|
| Meaning | the original ends of links to signals, parameters and issues, as the source writes them |
| Note | for treporting itself, `issue_ids` would hold the link to the tickets - where it cannot be derived the other way round |

The other types follow.
