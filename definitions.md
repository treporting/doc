# Definitions

The terms used in the requirements and the architecture of treporting.

## System

A system - SVN, GIT, JIRA, CONFLUENCE, ARTIFACTORY, DOORS, CODEBEAMER and others - is anything
that items can be stored in. It should not delete items once stored, it gives revisions to single
items, and it can create a baseline: a label for a selected group of items, each at a certain
revision.

A revision is unique within its system. Different systems name it differently: SVN a revision,
GIT a commit id, DOORS a baseline, JIRA a change id per issue, CODEBEAMER a version per item. A
system returns an item by its revision.

The revision tells changes of the same item apart - first stored: revision 1, changed: revision 2,
changed again: revision n - and identifies when and by whom a change was made.

A system is named in the stored data by the name it has in the configuration of the project, not
by its address. Where the data sits below the system rather than at it, the name carries the rest
of the path, such as `ACME-GIT/team/repo`. A list separated by commas is legitimate: it says that
the data may lie in the one and/or the other system.

There are two kinds of system. A **file-based** system - SHAREPOINT, SVN, GIT, JFROG - only
manages files; the content lies in the folders and files themselves. An **attribute-based**
system - DOORS, JIRA, a DMS, CODEBEAMER - holds items whose attributes each customer customizes.

**The storage is ours.** A system is where the data comes from; the storage is where treporting
puts it.

## Item

An item is an entity that can be identified uniquely within a system. Its name depends on the
system: DOORS has modules, SVN and GIT have files, JIRA and CODEBEAMER have tickets or issues.

## Content

An item is the envelope of its content: requirements described in text, tables or graphs, an
architecture, software, electrical or mechanical engineering tasks, test cases, decisions. The
content is everything a process needs - any kind of information.

## Process

A process is the ideal statement of what has to be done, when and by whom, to realize a product -
from the idea to the realization. It splits the development of a product into smaller pieces.

- It defines work products.
- It defines the relations and dependencies between them: a specification has to be there to
  create an architecture or a test case; an architecture has to be there to create an
  implementation; an implementation has to be there to run a test case against.
- It defines roles and responsibilities: the test manager creates the test plan and the test
  reports; the tester creates and runs the tests.

A process defined by a company is mostly used by many projects, so that people find their way in
different projects and use the same words. Each domain has its standardized processes, listed in
[standards.md](standards.md). The process of the company has to match the standardized one, which
a process audit evaluates. The goal of a project, beside its daily work, is to apply the process
of the company and so to fulfil the standardized one, which a project audit evaluates. Audits use
models of process assessment and improvement.

## Work product

A work product is a logical entity: it says what a concrete item is for. Several items may belong
together and form one work product.

- System DOORS: several modules can hold the requirements of the ASPICE level SYS.1.
- System GIT or SVN: several files can hold the information of one unit, module or component.
- System GIT or SVN, work product unit test results: all items holding unit test results for the
  architectural entities called units. They may be spread over the structure of folders.

A naming scheme and a default structure map the location of an item in its system to its work
product.

A work product has a role, which is a logical unit (specification, implementation, test) or an
organizational one - one more layer of grouping. A work product needs someone responsible, for
the milestones and for the access rights in the system.

## Scope

A scope is a group of work products for a purpose defined by the process.

## Project

A project is every effort aimed at completing a product to be delivered.

```
Organization
  │
  └── RProject ─── Release          requirements are specified
        │
        └── LProject ─── Library    a set of requirements is implemented
```

Requirements and tests are defined and realized with their own process and milestones; a full
cycle is a release. The architecture breaks a system down into subsystems, which are realized in
subprojects called LProjects. Every LProject has its own process and milestones; a full cycle is a
library.

An LProject belongs to the RProject it was split off from and stays for the life of it: a control
unit is a subsystem of one vehicle project and outlives its releases. A release and a library are
two branches beside one another, not one inside the other - spans of time, each at its own pace.
Which library a release was delivered with is therefore not read off the two; the baseline says
it, because it names both.

## Release and library

A release or a library is a span of time in which a process is used to do the work that adds to
the content of the product. *Release* is used for the product, *library* for a part of it, mostly
software. A product mostly needs several releases, one after another, to be finished.

## Milestone

A milestone is a point in time. A release is broken down into milestones to match internal or
external needs; they show who does what by when.

Ideally a milestone, the *what*, matches a scope of work products. A milestone may deliver work
products of several scopes (1:n), and a scope may hold work products delivered at different
milestones (n:1).

## Architectural breakdown

Architecture is the breakdown of the product into small pieces, and the definition of how those
pieces communicate. For software the entities are subsystem → 1:n → component → 1:n → module →
1:n → unit → 1:n → function. The breakdown depends on the context, code-based or model-based, and
on knowledge of the domain. A work product can be related to one architectural entity. An
architectural entity is realized by the content of items in a system.

## Baseline

A baseline labels, groups and identifies several work products.

- DOORS: several modules, each at its own revision, are completed by a date and grouped with the
  label "valid for release x.y.z", for instance in the comment of the DOORS baseline.
- GIT: several files are completed by a date and grouped with the tag "library x.y.z".

The labels *release* (product) and *library* (part of it) form the baselines.

### Which revision belongs to which baseline

There is a planned date and an actual date. To know which revision of a work product belongs to
which release or library, a reference is needed, such as a delivery list or a version object in
JIRA with its release date. With only a planned date, the youngest revision just before it can
only be **guessed** to be the one used - and the guess may be wrong.

## Traceability

Traceability is the establishment of relations between work products and their content. It makes
it possible

- to verify that work products exist, or do not,
- to report the state of work products at defined scopes - milestones, releases,
- to determine the dependencies between work products,
- to prove the maturity of the process.

A formal process may, for instance, ask for requirements-based testing. Then first the
requirements are needed, then the test cases, and at execution the test results. The work goes
downstream: requirement → test case → test result. The traces are mostly made upstream only:
requirement ← test case ← test result - every test case names the requirement it is for, every
test result the test case it is for.

Traceability is the base for knowing which requirement is tested, and with which result. The
matrix of requirements and tests

| tests vs requirements | requirement-1 | requirement-2 | requirement-3 |
|---|---|---|---|
| test case-1 | pass | - | - |
| test case-2 | - | pass | - |
| test case-3 | - | - | fail |

can be one reference for the decision to release a product. Traceability serves

- test management, to set priorities,
- change management, to analyse the impact of a change and to estimate and plan the effort,
- risk management, to analyse risks,
- problem management, for a first analysis of root causes,
- product management, to create a roadmap and to find a minimum viable product,
- quality assurance, to determine the maturity of the product and to state KPIs,
- configuration management, to determine the state of work products.
