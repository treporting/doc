# User needs (r1)

What each role needs from treporting, without naming a solution. The system requirements (r2)
are derived from these.

The needs themselves - ids `UN-<role>-nn` - are in [user-needs.yaml](user-needs.yaml), in the format
of [formats.md](../formats.md); each section is a role, the field `function` of a need.

## Project Manager - PM

`UN-PM-01` to `UN-PM-03`: in [user-needs.yaml](user-needs.yaml).

## Release Manager - RM

`UN-RM-01` to `UN-RM-05`: in [user-needs.yaml](user-needs.yaml).

## Configuration Manager - CM

`UN-CM-01` to `UN-CM-04`: in [user-needs.yaml](user-needs.yaml).

## Quality Assurance - QA

`UN-QA-01` to `UN-QA-04`: in [user-needs.yaml](user-needs.yaml).

## Safety - SAF

`UN-SAF-01` to `UN-SAF-03`: in [user-needs.yaml](user-needs.yaml).

## Assessor - ASR

`UN-ASR-01` to `UN-ASR-07`: in [user-needs.yaml](user-needs.yaml).

## Developer - DEV

`UN-DEV-01`: in [user-needs.yaml](user-needs.yaml).

## Tester - TST

`UN-TST-01` to `UN-TST-02`: in [user-needs.yaml](user-needs.yaml).

## Operator - OPS

`UN-OPS-01` to `UN-OPS-13`: in [user-needs.yaml](user-needs.yaml).

## Configurator - CFG

Whoever sets treporting up for the systems of a customer.

`UN-CFG-01` to `UN-CFG-03`: in [user-needs.yaml](user-needs.yaml).

## All roles - ALL

`UN-ALL-01` to `UN-ALL-04`: in [user-needs.yaml](user-needs.yaml).

## Safety of the product - PSF

What every role relies on when it decides on what treporting shows. treporting controls
nothing, but a gap it hides can lead to a wrong release. The hazards they control are in
`safety/hazard-and-risk-analysis.md`; the analysis of the tool's failures (#12) traces to these needs.

`UN-PSF-01` to `UN-PSF-06`: in [user-needs.yaml](user-needs.yaml).
