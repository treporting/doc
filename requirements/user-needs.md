# User needs (r1)

What each role needs from treporting, without naming a solution. The system requirements (r2)
are derived from these.

The ids are `UN-<role>-nn`. The format of this file is preliminary until #6 defines it.

## Project Manager - PM

| Id | Need |
|---|---|
| UN-PM-01 | Sees how far each feature has got, down all levels, in a release. |
| UN-PM-02 | Narrows any view to the functions, features and priorities of the own scope. |
| UN-PM-03 | Sees where the chain from requirement to test result breaks, to plan the work there. |

## Release Manager - RM

| Id | Need |
|---|---|
| UN-RM-01 | Sees which of its requirements are not yet backed by passed tests. |
| UN-RM-02 | Sees whether maturity grows from release to release and from library to library. |
| UN-RM-03 | Knows which build and which data a report was made from. |
| UN-RM-04 | Hands a report on to people who do not use the system. |
| UN-RM-05 | Approves a release, and may use the reported data as information for it. |

## Configuration Manager - CM

| Id | Need |
|---|---|
| UN-CM-01 | Knows which documents, at which revision, belong to which baseline. |
| UN-CM-02 | Knows which tool holds which documents. |
| UN-CM-03 | Sees what changed from one baseline to the next. |
| UN-CM-04 | Sees how a vehicle project is split into subsystems, and its releases and libraries over time. |

## Quality Assurance - QA

| Id | Need |
|---|---|
| UN-QA-01 | Follows the trace from user need over requirements to test cases and their results, both ways. |
| UN-QA-02 | Sees the maturity of each level, comparable over releases. |
| UN-QA-03 | Sees the state of the tests by kind (test case, procedure, result) and by test level (MiL to HiL). |
| UN-QA-04 | Reads the same data in the vocabulary of the development process in use. |

## Safety - SAF

| Id | Need |
|---|---|
| UN-SAF-01 | Shows that every hazard is controlled by a measure, down to a test result. |
| UN-SAF-02 | Narrows to a safety class, the unclassified included. |
| UN-SAF-03 | Relies on a safety class being carried down the trace without gaps. |

## Assessor - ASR

| Id | Need |
|---|---|
| UN-ASR-01 | Sees which clauses of the standards chosen are addressed and verified, per release. |
| UN-ASR-02 | Can check the evidence: which revision, which data, how many objects. |
| UN-ASR-03 | Compares the project against a process reference model - ASPICE, DO-178C, EN 50716, IEC 62304, IEC 61508. |
| UN-ASR-04 | Sees who produced a report, when, from which data and revision, and with which parameters. |
| UN-ASR-05 | Sees every import or change of data - who, when, what - and the state before it. |
| UN-ASR-06 | Gets complete copies of the records, readable by people and by machines. |

## Developer - DEV

| Id | Need |
|---|---|
| UN-DEV-01 | Sees which of the requirements assigned to them have no code or no test yet. |

## Tester - TST

| Id | Need |
|---|---|
| UN-TST-01 | Knows from which requirements, up to the user need, a test is derived. |
| UN-TST-02 | Sees whether a requirement is already verified on another level. |

## Operator - OPS

| Id | Need |
|---|---|
| UN-OPS-01 | Runs it where no database server can be reached. |
| UN-OPS-02 | Brings together what is kept in different tools - DOORS, Git, SVN, codebeamer and others. |
| UN-OPS-03 | Keeps several data sets side by side and apart - generated data and data read in, each baseline on its own. |
| UN-OPS-04 | Gets it running without help from those who built it. |
| UN-OPS-05 | Moves to a new version without losing or changing the data. |
| UN-OPS-06 | Knows when it is not available, and why. |
| UN-OPS-07 | Finds the cause of a failure from what it recorded. |
| UN-OPS-08 | Gives access only to authorised people, each known by an identity of their own. |
| UN-OPS-09 | Keeps the records and their history for a set period, readable throughout. |

## All roles - ALL

| Id | Need |
|---|---|
| UN-ALL-01 | Understands what to do on a first look, without being told. |
| UN-ALL-02 | Knows whether the data shown is complete or still loading. |
| UN-ALL-03 | Knows which data set a view answers from. |
| UN-ALL-04 | Is recorded only for a stated purpose and period, and only those who need it see the record. |

## Safety of the product - PSF

What every role relies on when it decides on what treporting shows. treporting controls
nothing, but a gap it hides can lead to a wrong release. The analysis of the tool's failures
(#12) traces to these needs.

| Id | Need |
|---|---|
| UN-PSF-01 | Relies on a gap in the trace never being shown as covered. |
| UN-PSF-02 | Relies on what is unknown being shown as unknown - never as zero, empty or passed. |
| UN-PSF-03 | Relies on a filter never hiding an object without saying so. |
| UN-PSF-04 | Relies on being told of every error that occurred while the data was read in. |
| UN-PSF-05 | Relies on every figure measuring what its label says. |
| UN-PSF-06 | Gets the same report from the same data and revision. |
