# Hazard and risk analysis

The hazards treporting can cause, by the method of IEC 61508-1, 7.4. treporting controls nothing; it is a
tool that people rely on when they decide on a release. Its hazards are therefore wrong
information that leads to a wrong decision - a product released with a gap that treporting did
not show.

The hazards are on level h1, with the ids `HAZ-nn`; the threats of security share that level
with the ids `THR-nn` (#22). Each hazard is controlled by a measure on level h2, with the ids
`HAZC-nn` - the prefix of the hazard and C for control -, and each measure asks for the user needs (r1) that realize it - mostly those of the
section Safety of the product (PSF) in `requirements/user-needs.md`. The tool
qualification package (#12) builds its analysis of tool errors on this file.

## Hazards

| Id | Hazard | Cause | Effect | Controlled by (h2) |
|---|---|---|---|---|
| HAZ-01 | a gap in the trace is shown as covered | a link, test case or test result missing in the data, or lost at the import | a requirement without passed test is taken as verified | HAZC-01 |
| HAZ-02 | an unknown value is shown as zero, empty or passed | a value missing in the source turned into a default at the import or in a view | a state is taken as known that is not | HAZC-02 |
| HAZ-03 | a filter hides objects without saying so | a filter on an attribute an object does not carry, a spelling that differs | a gap outside the view is not seen | HAZC-03 |
| HAZ-04 | an error while reading goes unreported | an extractor or converter ends without reporting what it could not read | the data looks complete and is not | HAZC-04 |
| HAZ-05 | a figure measures something else than its label says | a maturity read off a level name, a chart counting what the table does not | a release is judged by a number that means something else | HAZC-05 |
| HAZ-06 | the same data gives another report | a rule changed without trace, data changed between two reports | a decision cannot be followed back to what it relied on | HAZC-06 |
| HAZ-07 | a safety class is lost or lowered down the trace | an inherited class not carried down, a lower class without decomposition | a safety-relevant requirement is treated as QM | HAZC-07 |

## Measures

| Id | Measure | Controls | Asks for (r1) | Realized by (r2) |
|---|---|---|---|---|
| HAZC-01 | a gap in the trace is marked as gap and never counted as covered | HAZ-01 | UN-PSF-01 | SYS-02, SYS-23, SYS-25, SYS-48 |
| HAZC-02 | an unknown value is kept and shown as unknown | HAZ-02 | UN-PSF-02 | SYS-26, SYS-28 |
| HAZC-03 | every view says which filters are in effect and what they leave out | HAZ-03 | UN-PSF-03 | SYS-10 |
| HAZC-04 | every import is counted on a way of its own, and every error is reported | HAZ-04 | UN-PSF-04 | SYS-22, SYS-23, SYS-26, SYS-29 |
| HAZC-05 | every figure is defined by what it counts, and its calculation is tested | HAZ-05 | UN-PSF-05 | SYS-30, SYS-45 to SYS-50 |
| HAZC-06 | every report records the data, revision and parameters it was made from | HAZ-06 | UN-PSF-06 | SYS-18, SYS-19, SYS-40, SYS-43 |
| HAZC-07 | a safety class is carried down the trace, and a lower one without decomposition is found | HAZ-07 | UN-SAF-03 | SYS-11, SYS-68, SYS-70 |

The detection itself is validated with faults built into data of known content (SYS-27).

## Risk

The severity of each hazard is that of the product a user releases on its information, which
treporting does not know. The risk is therefore kept low by detection rather than rated: every
hazard is either prevented by the requirements above, or made visible to the user, and the
detection itself is validated with faults built into data of known content (SYS-27).
