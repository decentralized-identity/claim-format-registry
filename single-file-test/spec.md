Template for a Registry Document
==================

**Registry Status:** Proposed

**Latest Draft:**
  [https://identity.foundation/claim-format-registry](https://identity.foundation/claim-format-registry)

Editors:
~ [Daniel Buchner](https://www.linkedin.com/in/dbuchner/) (Block)
~ [Brent Zundel](https://www.linkedin.com/in/bzundel/) (Evernym)
~ [Martin Riedel](https://www.linkedin.com/in/rado0x54/) (Identity.com)
~ [Kim Hamilton Duffy](https://www.linkedin.com/in/kimdhamilton/) (Centre Consortium)

Contributors:
~ [Juan Caballero](https://github.com/bumblefudge) ([Centre Consortium](https://centre.io))

Participate:
~ [GitHub repo](https://github.com/decentralized-identity/<profile-name>)
~ [File a bug](https://github.com/decentralized-identity/<profile-name>/issues)
~ [Commit history](https://github.com/decentralized-identity/<profile-name>/commits/master)

------------------------------------

## Abstract

This registry tracks canonical references to claim formats in the verifiable credential ecosystem for use by DIF specifications, i.e. [Presentation Exchange](https://identity.foundation/presentation-exchange/#claim-format-designations).

### Audience

Who is the audience for this document, and what can they trust/assume about the
document?

## Status of This Document

The structure (not the content) of this registry is classed as a PROPOSED
specification under development within the Decentralized Identity Foundation
(DIF).

NOTE: Until working group chairs have approved a registry (all fields complete
and detailed, registry structured, instructions for new entries written), the
status of a registry is PROPOSED.  Working Group chairs may escalate to the DIF
Steering Committee if they disagree about the readiness of a registry
definition, or if they are concerned about the implications of DIF approving
registry as-is.  Once approved, a registry is ACTIVE at long as it has one or
more responsible code-owners managing new PRs; working group chairs may switch a
registry to ARCHIVED or HIBERNATED if this stops being the case.

### Dependencies

Any upstream dependencies or specifications defining terminology used in what
follows should be listed to make more objective any judgments (particularly
about conformance or interoperability) implied by presence in the registry. Be
explicit about conformance testing (and versions thereof), for example, where
versioned conformance tests have been published.

### Structure of the Registry 

Each row represents a "format," i.e. a set of possible envelopes and signing mechanisms for claims.  The columns are defined as follows:
* Abbreviation: A short string without whitespace used as reference for a format.
* AKA: Also known as...
* Description: A narrative description
* `alg`: A list of algorithm references from the JW* family of tokens (defined in [RFC7518sec3][]) that may be supported within the format. 
* `proof_type`: A list of Linked-Data integrity proof types (defined in the [Data-Integrity][] draft specification, a work item of the Verifiable Credentials working group at the W3C) that may be supported within the format.

### Additional Instructions for Registrants

Please mention in PR commentary the implementers using the claim format being added and a rationale for the abbreviations and `alg`/`proof_type` naming conventions used.

### Conditions for Rejection or Removal

Maintainers reserve the right to reject, remove, or delay acceptance of PRs. 

## Registry 

|`jwt`|"Vanilla JWT"|The format is a JSON Web Token (JWT) as defined by [RFC7519][] that will be submitted in the form of a JWT encoded string. Expression of supported algorithms in relation to this format MUST be conveyed using an alg property paired with values that are identifiers from the JSON Web Algorithms registry [RFC7518][].|See [RFC7518sec3][]|n/a|
|`jwt_vc`,`jwt_vp`|"JWT VC/VP"|These formats are JSON Web Tokens (JWTs) [RFC7519][] that will be submitted in the form of a JWT-encoded string, with a payload extractable from it defined according to the JSON Web Token (JWT) [section] of the W3C [VC-DATA-MODEL][] specification. Expression of supported algorithms in relation to these formats MUST be conveyed using an JWT `alg` property paired with values that are identifiers from the JSON Web Algorithms registry in [RFC7518-sec3][].|See [RFC7518sec3][]|n/a|
|`ldp`|"Linked Data Proof"|The format is a Linked-Data Proof that will be submitted as an object. Expression of supported algorithms in relation to these formats MUST be conveyed using a `proof_type` property with values that are identifiers from the Linked Data Cryptographic Suite Registry ([LDP-Registry][]).|n/a|See [LDP-Registry][]|
|`ldp_vc`, `ldp_vp`|"Linked-Data VC/VP"|Verifiable Credentials or Verifiable Presentations signed with Linked Data Proof formats. These are descriptions of formats normatively defined in the W3C Verifiable Credentials specification [VC-DATA-MODEL][], and will be submitted in the form of a JSON object. Expression of supported algorithms in relation to these formats MUST be conveyed using a proof_type property paired with values that are identifiers from the Linked Data Cryptographic Suite Registry ([LDP-Registry][]).|n/a|See [LDP-Registry][]|
|`ac_vc`,`ac_vp`|"AnonCreds VC/VP"|Verifiable Credentials or Verifiable Presentations made using the CL-signature scheme. Specification of AnonCreds is currently underway at the Anon-Creds WG ([anoncreds-wg][https://github.com/AnonCreds-WG]).|n/a|`CLSignature2019`|

[RFC7518]: https://datatracker.ietf.org/doc/html/rfc7518
[RFC7518sec3]: https://datatracker.ietf.org/doc/html/rfc7518#section-3
[RFC7519]: https://datatracker.ietf.org/doc/html/rfc7519
[VC-DATA-MODEL]: https://w3c.github.io/vc-data-model/
[LDP-Registry]: https://w3c-ccg.github.io/ld-cryptosuite-registry/
[Data-Integrity]: https://w3c-ccg.github.io/data-integrity-spec/
[anoncreds-wg]: https://github.com/AnonCreds-WG/anoncreds-spec