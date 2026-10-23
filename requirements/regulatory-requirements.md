# Regulatory requirements

What standards and laws ask of treporting. They stand beside the user needs (r1): they do not come
from a role, and they hold whether a user asks for them or not. The system requirements (r2) are
derived from both, and every regulatory requirement has at least one system requirement.

The ids are `REG-nn`. The format of this file is preliminary until #6 defines it.

Each line says in own words what the clause asks; the clause itself is authoritative. Which of them
apply to a project is decided by the organization that uses treporting, by its domain.

## Tool qualification

treporting controls nothing, but it can fail to show a gap - a tool that people rely on when they
release.

| Id | Source | Asks | Applies to | Realized by |
|---|---|---|---|---|
| REG-01 | ISO 26262-8, clause 11 | classify a software tool by its impact and by how surely its errors are detected (TI, TD, TCL), and qualify it where the confidence level is TCL2 or TCL3 | automotive | SYS-23, SYS-24, SYS-25, SYS-26, SYS-27 |
| REG-02 | IEC 61508-3, 7.4.4 | show that an offline support tool of class T2, which can fail to reveal a defect, is fit for its use | industry, railway (EN 50716) | SYS-23, SYS-24, SYS-25, SYS-26, SYS-27 |
| REG-03 | DO-330 | qualify a verification tool whose output is not verified otherwise | airborne | SYS-23, SYS-24, SYS-25, SYS-26, SYS-27 |
| REG-04 | ISO 13485, 4.1.6 | validate software used in the quality management system before its first use and after changes | medical | SYS-27 |

## Electronic records

| Id | Source | Asks | Applies to | Realized by |
|---|---|---|---|---|
| REG-05 | 21 CFR 11.10(e) | keep a secure, computer-generated audit trail with time stamps of every creation, change and deletion of a record, without hiding what was there before | medical (FDA) | SYS-40, SYS-41 |
| REG-06 | 21 CFR 11.10(d), (g) | let only authorised people use the system, and check their authority for what they do | medical (FDA) | SYS-39 |
| REG-07 | 21 CFR 11.10(b) | produce accurate and complete copies of records, readable by people and in electronic form | medical (FDA) | SYS-32 |
| REG-08 | 21 CFR 11.10(c) | protect records so that they can be retrieved accurately throughout their retention period | medical (FDA) | SYS-42 |
| REG-09 | 21 CFR 11.50, 11.70 | an electronic signature shows the name of the signer, the time and its meaning, and is bound to its record so that it cannot be moved to another | medical (FDA) | SYS-43 |
| REG-10 | FDA, data integrity (ALCOA) | data are attributable, legible, contemporaneous, original and accurate - every figure can be followed back to whom and what it comes from | medical (FDA) | SYS-18, SYS-40, SYS-41 |

## Personal data and legal notice

| Id | Source | Asks | Applies to | Realized by |
|---|---|---|---|---|
| REG-11 | GDPR, Art. 5(1)(b), (e) | process personal data only for the purposes stated, and keep it no longer than they need | EU | SYS-44 |
| REG-12 | BetrVG, §87(1) no. 6 | a technical means that can monitor the behaviour or performance of employees needs the consent of the works council | Germany | SYS-44 |
| REG-13 | DDG, §5; GDPR, Art. 13 | a service on the internet names who runs it, and tells users what personal data it processes | Germany, EU | SYS-57 |
