# System requirements (r2)

What treporting has to do, seen as one box - viewer, reporter and storage together. Each
requirement names the user needs (r1) and the regulatory requirements (`regulatory-requirements.md`)
it comes from - or the decision of the architecture that made it possible -, and every need and
every regulatory requirement that treporting realizes has at least one requirement. How the
system does it is left to the architecture (r3).

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
| SYS-18 | show on every view and in every report which data set, which revision and which build of the system it answers from, and how many objects of each kind | UN-RM-03, UN-ASR-02, UN-ALL-03, REG-10 |
| SYS-19 | give the same report for the same data set, revision and parameters | UN-PSF-06 |
| SYS-20 | hold several data sets apart - generated data and data read in, each baseline on its own - and answer each request from exactly one of them | UN-OPS-03 |
| SYS-21 | answer from a data file when no database server can be reached | UN-OPS-01 |
| SYS-22 | read the data of different tools into one model, and name every object it could not read, with the reason | UN-OPS-02, UN-PSF-04 |

## Integrity

treporting controls nothing, but it can fail to show a gap (tool impact TI2 in ISO 26262-8,
clause 11). Whether it has to be qualified depends on how surely its own errors are detected: with
high confidence (TD1) the tool confidence level is TCL1 and no qualification is needed. IEC 61508
(class T2) and DO-330 argue alike. The requirements of this feature are what makes errors of an
import detectable.

The check has to be independent of the reading: a converter that counts what it reads shares every
error of the reading with its count. So the source is counted by a way of its own, and the storage
is counted after the import, not by the converter. Four levels together give the evidence:

| Level | What | Finds |
|---|---|---|
| A. reconciliation at every import | count at four points - in the source by a query of its own (the object count of a DOORS module, the total of a codebeamer query, a `git grep` for `@implements`), read, refused with a reason, stored; source = read + refused, read = stored; per kind of object, per type of link, per state | missing objects, missing links, states counted wrong |
| B. content check | a fingerprint of the fields that matter, per object, on the side of the source and on the side of the storage | attributes swapped, links to the wrong object, an unknown value turned into zero or empty |
| C. known-answer test per release | data sets of known content, with faults built in - missing objects, missing links, unknown values, spellings that differ; every fault has to be reported | that the checks find what they are for - the evidence for TD1 |
| D. reference edgedb (#9) | treporting reads its own repos; the expected counts come independently from git | real data instead of generated |

Equal counts do not prove the content right - that is level B. That the checks find anything at all
is shown by level C only.

| Id | The system shall | From |
|---|---|---|
| SYS-23 | count at every import, per kind of object, per type of link and per state, at four points - in the source by a query of its own, read, refused, and stored, counted from the storage afterwards - and name every difference | UN-PSF-01, UN-PSF-04, REG-01, REG-02, REG-03 |
| SYS-24 | build the same data set from the same source on every import | UN-PSF-06, REG-01, REG-02, REG-03 |
| SYS-25 | compare at every import a fingerprint of the fields that matter of each object in the source with the same object as stored, and name every object that differs | UN-PSF-01, UN-PSF-02, REG-01, REG-02, REG-03 |
| SYS-26 | mark every data set as complete, incomplete when its import showed a difference, or unverified when its source could not be counted on a way of its own - on every view and in every report that answers from it | UN-PSF-02, UN-PSF-04, REG-01, REG-02, REG-03 |
| SYS-27 | report, in every release, every fault built into a data set of known content - a missing object, a missing link, an unknown value, a spelling that differs | REG-01, REG-02, REG-03, REG-04 |

## Errors

| Id | The system shall | From |
|---|---|---|
| SYS-28 | show a value that is unknown as unknown, distinct from zero, empty or passed | UN-PSF-02 |
| SYS-29 | refuse a request it cannot answer, with the reason, rather than answer it empty | UN-PSF-02, UN-PSF-04 |
| SYS-30 | say for every figure what it counts, and count in a chart exactly what the table beside it shows | UN-PSF-05 |

## Export

| Id | The system shall | From |
|---|---|---|
| SYS-31 | export every table in a machine-readable format and every chart as a picture | UN-RM-04, UN-ASR-06 |
| SYS-32 | export complete records with their history, readable by people and by machines | UN-ASR-06, REG-07 |

## Usability

| Id | The system shall | From |
|---|---|---|
| SYS-33 | say on the first screen what it does and where to start, and lead back there from any view | UN-ALL-01 |
| SYS-34 | show while a view is loading, or while the data is not there yet, that it is, and fill the view by itself when the data arrives | UN-ALL-02 |

## Operation

| Id | The system shall | From |
|---|---|---|
| SYS-35 | be installed and started from a release by following its operator manual alone | UN-OPS-04 |
| SYS-36 | keep the data unchanged when moved to a new version, and say before the move which data the new version cannot read | UN-OPS-05 |
| SYS-37 | tell the user when it, or a part of it, is not available, and why | UN-OPS-06 |
| SYS-38 | record its errors and warnings with time and cause | UN-OPS-07 |

## Audit

| Id | The system shall | From |
|---|---|---|
| SYS-39 | authenticate every user by an identity of their own, and grant access by role | UN-OPS-08, REG-06 |
| SYS-40 | record for every report who produced it, when, from which data set and revision, and with which parameters | UN-ASR-04, REG-05, REG-10 |
| SYS-41 | record every import and change of data - who, when, what - and keep the state before it; the record of an import holds the source and its revision, the time, who started it, the version of the converter, the counts at the four points of SYS-23, the objects refused with their reason, the result of the fingerprints of SYS-25 and the state of SYS-26 | UN-ASR-05, REG-05, REG-10 |
| SYS-42 | keep the records and their audit trail for a set period, readable throughout | UN-OPS-09, REG-08 |
| SYS-43 | give every report an identity of its own and a fingerprint of the data it was made from, so that a decision taken elsewhere - such as the approval of a release - can name the report it relied on | UN-RM-05, REG-10 |
| SYS-44 | use the record of what users did only for the purposes set, delete it after the period set, and show it only to the roles allowed to see it | UN-ALL-04, REG-11, REG-12 |

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
| SYS-45 | give the maturity of a requirement as the share of the steps of the longest chain it has reached | UN-RM-02, UN-QA-02 |
| SYS-46 | give the maturity of each group - RG-SYS-R, RG-SW-R, RG-SC, RG-OC, RG-SW-TC, RG-SW-TR, RG-SYS-TC, RG-SYS-TR - as the share of the steps of that group reached | UN-RM-02, UN-QA-02 |
| SYS-47 | count a test result as reached only when it passed | UN-PSF-05 |
| SYS-48 | count a step as reached only when every branch below the requirement reaches it | UN-PSF-01 |
| SYS-49 | take the longest chain from the process reference model in use and the coverage levels coded for source code and object code - ASPICE with one level each, 20 steps, when none is chosen - and leave out every step whose level holds no object in the release; every report states the chain it used and the steps it left out | UN-QA-04, UN-ASR-03, UN-PSF-05, UN-ASR-02 |
| SYS-50 | give the maturity of a level, a feature or a release as the mean of the maturity of its requirements | UN-RM-02, UN-QA-02 |

## Performance

The non-functional requirements. Their figures are measured first on the prototype with generated
data, then set as targets (#16); until then they read *open*. A requirement of another feature that
depends on a figure refers to the requirement here.

The sizes of a data set:

| Size | Requirements | Links | Test results | Baselines |
|---|---|---|---|---|
| small | open | open | open | open |
| medium | open | open | open | open |
| large | open | open | open | open |

| Id | The system shall | Measured | Target | From |
|---|---|---|---|---|
| SYS-51 | answer from a data set of size large | open | open | UN-OPS-02, UN-OPS-03 |
| SYS-52 | show a view of a data set of size large within the time given | open | open | UN-ALL-02 |
| SYS-53 | import a data set of size large, with the checks of Integrity, within the time given | open | open | UN-OPS-02 |
| SYS-54 | be ready to answer within the time given after it was started | open | open | UN-OPS-04, UN-OPS-06 |
| SYS-55 | run within the memory and the processor time given | open | open | UN-OPS-01, UN-OPS-04 |
| SYS-56 | serve the number of users given at once, each within the time of SYS-52 | open | open | UN-OPS-08 |

## Constraints

| Id | The system shall | From |
|---|---|---|
| SYS-57 | carry a legal notice and a privacy notice on every page reachable from the internet | REG-13 |

## Licensing

Priority **later**: treporting has no licensed feature yet - everything is under Apache-2.0
(#24). These requirements keep the way open for features developed for customers. A feature
meant to be licensed must not be published under Apache-2.0 before, or it stays free for good.

| Id | The system shall | From |
|---|---|---|
| SYS-58 | check, on every request to a licensed feature, the role and the rights of the user and the licence of the installation, and refuse the request with the reason when one of them is missing | UN-OPS-10 |
| SYS-59 | show which features an installation is licensed for | UN-OPS-10 |

## Configuration

| Id | The system shall | From |
|---|---|---|
| SYS-60 | take the mapping of attributes and values from a configuration file per system of a customer, and take code of the customer, kept outside the core, only where a configuration cannot say it | UN-CFG-01 |
| SYS-61 | check a configuration against the data of its system, and name every attribute and every value it does not map | UN-CFG-02 |
| SYS-62 | read the configurations and the catalogues of the customer - such as the mapping of the clauses of a standard to work products - from a place the operator sets, outside the installation of the product | UN-CFG-03 |

## Delivery

| Id | The system shall | From |
|---|---|---|
| SYS-63 | come with an SBOM in every release, naming each component, its version and its licence, and with the licence texts and notices of the components | UN-OPS-12, REG-14, REG-15, REG-18 |
| SYS-64 | be delivered with a secure configuration by default | REG-14 |
| SYS-65 | be updatable to a release that fixes a vulnerability, without other changes coming with it | UN-OPS-11, REG-14, REG-15 |
| SYS-66 | state the period over which a release gets security fixes | UN-OPS-11, REG-17 |
| SYS-67 | name, in every release and on the demo, where a vulnerability is reported and how it is handled | UN-OPS-13, REG-15 |

## Derived values

| Id | The system shall | From |
|---|---|---|
| SYS-68 | keep every value as read from its source, and keep a value it derives beside it under a name of its own - `M` for mapped, `I` for inherited -, and say on every view which of the two it shows | UN-PSF-05, UN-SAF-03, REG-10 |
| SYS-69 | make the derived values of a stored data set again on request when a rule changes, back in time, without fetching the data from the source systems again | architecture: original and derived values |

## Plausibility

| Id | The system shall | From |
|---|---|---|
| SYS-70 | analyse a data set, as a report, against rules of plausibility - a child with a lower safety class than its parent and no decomposition, an unclassified child under a classified parent, a passed test result without a test case, a cycle in the trace, a link into another baseline; the import reads the data as it is and is never stopped or changed by such a finding | UN-SAF-01, UN-SAF-03, UN-PSF-01, REG-19, REG-20, REG-21, REG-22 |
| SYS-71 | show every finding of SYS-70 with its rule and its objects, in a view of its own | UN-SAF-01, UN-PSF-03 |
| SYS-72 | recognize a finding as evaluated when its object carries an evaluation in its source - an attribute or a link set by the configuration -, and show for every finding whether it is evaluated or open, with the evaluation | UN-ASR-07, UN-SAF-01, REG-10 |

## Open

- **Figures**: the measured and the target figures in the tables of [Performance](#performance) (#16).
