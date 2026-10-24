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

The other attributes of Requirement and the other types follow.
