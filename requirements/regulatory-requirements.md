# Regulatory requirements

What standards and laws ask of treporting. They stand beside the user needs (r1): they do not come
from a role, and they hold whether a user asks for them or not. The system requirements (r2) are
derived from both, and every regulatory requirement that treporting realizes has at least one system requirement; one it does not realize says why.

The requirements themselves - ids `REG-nn` - are in
[regulatory-requirements.yaml](regulatory-requirements.yaml), in the format of
[formats.md](../formats.md); each section is the field `category`. Which system requirements
realize one is read from their uplinks; one that treporting does not realize says why in
`not_realized`.

Each line says in own words what the clause asks; the clause itself is authoritative. Which of them
apply to a project is decided by the organization that uses treporting, by its domain.

## Tool qualification

treporting controls nothing, but it can fail to show a gap - a tool that people rely on when they
release.

`REG-01` to `REG-04`: in [regulatory-requirements.yaml](regulatory-requirements.yaml).

## Electronic records

`REG-05` to `REG-10`: in [regulatory-requirements.yaml](regulatory-requirements.yaml).

## Personal data and legal notice

`REG-11` to `REG-13`: in [regulatory-requirements.yaml](regulatory-requirements.yaml).

## Safety classes

`REG-19` to `REG-22`: in [regulatory-requirements.yaml](regulatory-requirements.yaml).

## Products on the market

treporting is open source, with the possibility of licensed features, and offered commercially. Whether and from
when the Cyber Resilience Act applies to it is to be confirmed by legal advice.

`REG-14` to `REG-18`: in [regulatory-requirements.yaml](regulatory-requirements.yaml).
