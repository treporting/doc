# Hazard and risk analysis

The hazards treporting can cause, after IEC 61508-1, 7.4. treporting controls nothing; it is a
tool that people rely on when they decide on a release. Its hazards are therefore wrong
information that leads to a wrong decision - a product released with a gap that treporting did
not show.

The ids are `HAZ-nn`. Each hazard is controlled by the needs of the section Safety of the product
(PSF) in `requirements/user-needs.md` and by the system requirements realizing them. The tool
qualification package (#12) builds its analysis of tool errors on this file.

## Hazards

| Id | Hazard | Cause | Effect | Controlled by |
|---|---|---|---|---|
| HAZ-01 | a gap in the trace is shown as covered | a link, test case or test result missing in the data, or lost at the import | a requirement without passed test is taken as verified | UN-PSF-01; SYS-02, SYS-23, SYS-25, SYS-48 |
| HAZ-02 | an unknown value is shown as zero, empty or passed | a value missing in the source turned into a default at the import or in a view | a state is taken as known that is not | UN-PSF-02; SYS-28, SYS-26 |
| HAZ-03 | a filter hides objects without saying so | a filter on an attribute an object does not carry, a spelling that differs | a gap outside the view is not seen | UN-PSF-03; SYS-10 |
| HAZ-04 | an error while reading goes unreported | an extractor or converter ends without reporting what it could not read | the data looks complete and is not | UN-PSF-04; SYS-22, SYS-23, SYS-26, SYS-29 |
| HAZ-05 | a figure measures something else than its label says | a maturity read off a level name, a chart counting what the table does not | a release is judged by a number that means something else | UN-PSF-05; SYS-30, SYS-45 to SYS-50 |
| HAZ-06 | the same data gives another report | a rule changed without trace, data changed between two reports | a decision cannot be followed back to what it relied on | UN-PSF-06; SYS-18, SYS-19, SYS-40, SYS-43 |
| HAZ-07 | a safety class is lost or lowered down the trace | an inherited class not carried down, a lower class without decomposition | a safety-relevant requirement is treated as QM | UN-SAF-03; SYS-11, SYS-68, SYS-70 |

## Risk

The severity of each hazard is that of the product a user releases on its information, which
treporting does not know. The risk is therefore kept low by detection rather than rated: every
hazard is either prevented by the requirements above, or made visible to the user, and the
detection itself is validated with faults built into data of known content (SYS-27).
