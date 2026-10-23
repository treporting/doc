# System requirements (r2)

What treporting has to do, seen as one box - viewer, reporter and storage together. Each
requirement names the user needs (r1) it comes from, and every need has at least one
requirement. How the system does it is left to the architecture (r3).

The ids are `SYS-nn`. The format of this file is preliminary until #6 defines it.

Each section is a feature, named by a short keyword. A requirement carries the functions of the
needs it comes from - the roles of `user-needs.md` - and the feature of its section.

## Trace

| Id | The system shall | From |
|---|---|---|
| SYS-01 | show the trace from any level chosen - user need, requirement, test or hazard - up and down to the test results, per release and library | UN-QA-01, UN-TST-01, UN-PM-03 |
| SYS-02 | mark every place in the trace where a link, a test case or a test result is missing, and never count such a place as covered | UN-PM-03, UN-RM-01, UN-PSF-01 |
| SYS-03 | show per release the requirements that are not yet verified by a passed test result | UN-RM-01 |
| SYS-04 | show per feature its state on every level below it, per release | UN-PM-01 |
| SYS-05 | count the states of each level per release and library, so that two releases or two libraries can be compared | UN-QA-02, UN-RM-02 |
| SYS-06 | show for a requirement on which other levels it is verified, and by which tests | UN-TST-02 |
| SYS-07 | show per person responsible the requirements assigned to them that have no implementation or no test | UN-DEV-01 |
| SYS-08 | tell test cases, test procedures and test results apart, each with its test level | UN-QA-03 |

## Filter

| Id | The system shall | From |
|---|---|---|
| SYS-09 | narrow every view by function, feature, priority and safety class, the unclassified included, the same way in table and chart | UN-PM-02, UN-SAF-02 |
| SYS-10 | show on every view which filters are in effect and how many objects they leave out | UN-PSF-03 |
| SYS-11 | carry function, feature, priority and safety class down the trace; where a requirement has several parents, it carries the highest safety class among them | UN-SAF-03, UN-PM-02 |

## Hazards

| Id | The system shall | From |
|---|---|---|
| SYS-12 | trace each hazard over its measures to the requirements and test results, and mark a hazard that has no measure or no passed result | UN-SAF-01 |

## Standards

| Id | The system shall | From |
|---|---|---|
| SYS-13 | show per clause of a chosen standard whether it is open, addressed or verified, per release | UN-ASR-01 |
| SYS-14 | show one data set in the vocabulary of a chosen process reference model - ASPICE, DO-178C, EN 50716, IEC 62304, IEC 61508 | UN-QA-04, UN-ASR-03 |

## Baselines

| Id | The system shall | From |
|---|---|---|
| SYS-15 | list per baseline its documents with their revision, their kind and the tool they are kept in | UN-CM-01, UN-CM-02 |
| SYS-16 | show what changed between two baselines: objects and documents added, removed or changed | UN-CM-03 |
| SYS-17 | show releases and libraries over time, and the split of a project into subsystems | UN-CM-04, UN-RM-02 |

## Provenance

| Id | The system shall | From |
|---|---|---|
| SYS-18 | show on every view and in every report which data set, which revision and which build of the system it answers from, and how many objects of each kind | UN-RM-03, UN-ASR-02, UN-ALL-03 |
| SYS-19 | give the same report for the same data set, revision and parameters | UN-PSF-06 |
| SYS-20 | hold several data sets apart - generated data and data read in, each baseline on its own - and answer each request from exactly one of them | UN-OPS-03 |
| SYS-21 | answer from a data file when no database server can be reached | UN-OPS-01 |
| SYS-22 | read the data of different tools into one model, and name every object it could not read, with the reason | UN-OPS-02, UN-PSF-04 |
| SYS-23 | compare, for every import, the number of objects of each kind read with the number in the source, and name every difference | UN-PSF-01, UN-PSF-04 |
| SYS-24 | build the same data set from the same source on every import | UN-PSF-06 |

## Errors

| Id | The system shall | From |
|---|---|---|
| SYS-25 | show a value that is unknown as unknown, distinct from zero, empty or passed | UN-PSF-02 |
| SYS-26 | refuse a request it cannot answer, with the reason, rather than answer it empty | UN-PSF-02, UN-PSF-04 |
| SYS-27 | say for every figure what it counts, and count in a chart exactly what the table beside it shows | UN-PSF-05 |

## Export

| Id | The system shall | From |
|---|---|---|
| SYS-28 | export every table in a machine-readable format and every chart as a picture | UN-RM-04, UN-ASR-06 |
| SYS-29 | export complete records with their history, readable by people and by machines | UN-ASR-06 |

## Usability

| Id | The system shall | From |
|---|---|---|
| SYS-30 | say on the first screen what it does and where to start, and lead back there from any view | UN-ALL-01 |
| SYS-31 | show while a view is loading, or while the data is not there yet, that it is, and fill the view by itself when the data arrives | UN-ALL-02 |

## Operation

| Id | The system shall | From |
|---|---|---|
| SYS-32 | be installed and started from a release by following its operator manual alone | UN-OPS-04 |
| SYS-33 | keep the data unchanged when moved to a new version, and say before the move which data the new version cannot read | UN-OPS-05 |
| SYS-34 | tell the user when it, or a part of it, is not available, and why | UN-OPS-06 |
| SYS-35 | record its errors and warnings with time and cause | UN-OPS-07 |

## Audit

| Id | The system shall | From |
|---|---|---|
| SYS-36 | authenticate every user by an identity of their own, and grant access by role | UN-OPS-08 |
| SYS-37 | record for every report who produced it, when, from which data set and revision, and with which parameters | UN-ASR-04 |
| SYS-38 | record every import and change of data - who, when, what - and keep the state before it | UN-ASR-05 |
| SYS-39 | keep the records and their audit trail for a set period, readable throughout | UN-OPS-09 |
| SYS-40 | record an approval of a release with the approver, the time, its meaning and a fingerprint of what was approved, and never change an approval afterwards | UN-RM-05 |
| SYS-41 | use the record of what users did only for the purposes set, delete it after the period set, and show it only to the roles allowed to see it | UN-ALL-04 |

## Maturity

The maturity of a requirement is how far down the longest chain of the V-model it has got: the
share of the steps of the chain it has reached. The number of steps is not fixed: each process
reference model has its own chain, and source code and object code have a step for each coverage
level coded, such as sc1 function and sc2 statement coverage, or oc1 object and oc2 assembler
coverage. The table shows the chain of ASPICE; with one coverage level each it has 20 steps, so
each step is 5 %. A step whose level is empty is skipped and the others count more,
so that 100 % can always be reached.

| Order | Object | ASPICE | Group |
|---|---|---|---|
| 1 | stakeholder requirement | SYS.1 | RG-SYS-R |
| 2 | system requirement | SYS.2 | RG-SYS-R |
| 3 | system architecture | SYS.3 | RG-SYS-R |
| 4 | software requirement | SWE.1 | RG-SW-R |
| 5 | software architecture | SWE.2 | RG-SW-R |
| 6 | detailed design | SWE.3 | RG-SW-R |
| 7 | source code, one step per coverage level (sc1, sc2, ...) | SWE.3 | RG-SC |
| 8 | object code, one step per coverage level (oc1, oc2, ...) | build | RG-OC |
| 9 | test case, test result of the unit test | SWE.4 | RG-SW-TC, RG-SW-TR |
| 10 | test case, test result of the software integration test | SWE.5 | RG-SW-TC, RG-SW-TR |
| 11 | test case, test result of the software qualification test | SWE.6 | RG-SW-TC, RG-SW-TR |
| 12 | test case, test result of the system integration test | SYS.4 | RG-SYS-TC, RG-SYS-TR |
| 13 | test case, test result of the system qualification test | SYS.5 | RG-SYS-TC, RG-SYS-TR |
| 14 | test case, test result of the validation | VAL.1 | RG-SYS-TC, RG-SYS-TR |

| Id | The system shall | From |
|---|---|---|
| SYS-42 | give the maturity of a requirement as the share of the steps of the longest chain it has reached | UN-RM-02, UN-QA-02 |
| SYS-43 | give the maturity of each group - RG-SYS-R, RG-SW-R, RG-SC, RG-OC, RG-SW-TC, RG-SW-TR, RG-SYS-TC, RG-SYS-TR - as the share of the steps of that group reached | UN-RM-02, UN-QA-02 |
| SYS-44 | count a test result as reached only when it passed | UN-PSF-05 |
| SYS-45 | count a step as reached only when every branch below the requirement reaches it | UN-PSF-01 |
| SYS-46 | take the longest chain from the process reference model in use and the coverage levels coded for source code and object code - ASPICE with one level each, 20 steps, when none is chosen - and leave out every step whose level holds no object in the release; every report states the chain it used and the steps it left out | UN-QA-04, UN-ASR-03, UN-PSF-05, UN-ASR-02 |
| SYS-47 | give the maturity of a level, a feature or a release as the mean of the maturity of its requirements | UN-RM-02, UN-QA-02 |

## Constraints

| Id | The system shall | From |
|---|---|---|
| SYS-48 | carry a legal notice and a privacy notice on every page reachable from the internet | constraint (German law) |

## Open

- **Approval**: whether a signed git tag fulfils SYS-40 is decided by the architecture (#4).
- **Figures**: no requirement names a time, a size or an availability yet.
