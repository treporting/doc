# Regulatory requirements

What standards and laws ask of treporting. They stand beside the user needs (r1): they do not come
from a role, and they hold whether a user asks for them or not. The system requirements (r2) are
derived from both, and every regulatory requirement that treporting realizes has at least one system requirement; one it does not realize says why.

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
| REG-09 | 21 CFR 11.50, 11.70 | an electronic signature shows the name of the signer, the time and its meaning, and is bound to its record so that it cannot be moved to another | medical (FDA) | not realized: treporting signs nothing; an approval is made where the organization makes it, and can name the report it relied on (SYS-43) |
| REG-10 | FDA, data integrity (ALCOA) | data are attributable, legible, contemporaneous, original and accurate - every figure can be followed back to whom and what it comes from | medical (FDA) | SYS-18, SYS-40, SYS-41, SYS-43, SYS-68, SYS-72 |

## Personal data and legal notice

| Id | Source | Asks | Applies to | Realized by |
|---|---|---|---|---|
| REG-11 | GDPR, Art. 5(1)(b), (e) | process personal data only for the purposes stated, and keep it no longer than they need | EU | SYS-44 |
| REG-12 | BetrVG, §87(1) no. 6 | a technical means that can monitor the behaviour or performance of employees needs the consent of the works council | Germany | SYS-44 |
| REG-13 | DDG, §5; GDPR, Art. 13 | a service on the internet names who runs it, and tells users what personal data it processes | Germany, EU | SYS-57 |

## Safety classes

| Id | Source | Asks | Applies to | Realized by |
|---|---|---|---|---|
| REG-19 | ISO 26262-9, clause 5; ISO 26262-3, -4, -6 | a safety requirement inherits the ASIL of the requirement it is derived from; it may get a lower one only by an ASIL decomposition into independent requirements | automotive | SYS-70 |
| REG-20 | ARP4754B, development assurance level assignment; DO-178C, 2.3 | an item gets the development assurance level (IDAL) of the function it realizes (FDAL), and its software the software level that follows from it; a lower level only where independence between the items is shown | airborne | SYS-70 |
| REG-21 | IEC 61508-2, 7.4.3; IEC 61508-3, 7.4.2.8 to 7.4.2.10 | an element gets the SIL of the safety function it realizes; software elements of different SIL are all treated as of the highest one, unless their independence is shown | industry, railway (EN 50716) | SYS-70 |
| REG-22 | IEC 62304, 4.3; 5.3.5 | a software item gets the software safety class of the software system or item it is decomposed from; a lower class only with a documented rationale, such as a segregation of the items | medical | SYS-70 |

## Products on the market

treporting is open source with licensed features, offered commercially (#24). Whether and from
when the Cyber Resilience Act applies to it is to be confirmed by legal advice.

| Id | Source | Asks | Applies to | Realized by |
|---|---|---|---|---|
| REG-14 | CRA (EU) 2024/2847, Annex I Part I | a product with digital elements is placed on the market without known exploitable vulnerabilities, with a secure configuration by default, and can be secured by updates | EU, commercial | SYS-63, SYS-64, SYS-65 |
| REG-15 | CRA, Annex I Part II | the manufacturer handles vulnerabilities: keeps an SBOM, fixes without delay and free of charge, has a policy of coordinated disclosure and a contact for reports | EU, commercial | SYS-63, SYS-65, SYS-67 |
| REG-16 | CRA, Art. 14 | an actively exploited vulnerability is notified: an early warning within 24 hours, a notification within 72 hours, a final report later | EU, commercial | not realized: a duty of the manufacturer, kept by our work (harness) |
| REG-17 | CRA, Art. 13(8) | security updates are provided over a support period stated in advance, as a rule at least five years | EU, commercial | SYS-66 |
| REG-18 | licences of the components, e.g. Apache-2.0 §4 | a release hands on the licence texts and notices of every component it contains | all | SYS-63 |
