Claim Format Registry
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
~ [Gabe Cohen](https://www.linkedin.com/in/cohengabe/) (Block)

Participate:
~ [GitHub repo](https://github.com/decentralized-identity/claim-format-registry)
~ [File a bug](https://github.com/decentralized-identity/claim-format-registry/issues)
~ [Commit history](https://github.com/decentralized-identity/claim-format-registry/commits/main)

------------------------------------

## Abstract

This registry tracks canonical references to claim formats in the verifiable credential ecosystem for use by DIF specifications, i.e. [Presentation Exchange](https://identity.foundation/presentation-exchange/#claim-format-designations).

## Status of This Document

The structure (not the content) of this registry is classed as a ****PROPOSED****
specification under development within the Decentralized Identity Foundation
(DIF).

:::note
Until working group chairs have approved a registry (all fields complete
and detailed, registry structured, instructions for new entries written), the
status of a registry is ****PROPOSED****.  Working Group chairs may escalate to the DIF
Steering Committee if they disagree about the readiness of a registry
definition, or if they are concerned about the implications of DIF approving
registry as-is.  Once approved, a registry is ****ACTIVE**** at long as it has one or
more responsible code-owners managing new PRs; working group chairs may switch a
registry to ****ARCHIVED**** or ****HIBERNATED**** if this stops being the case.
:::

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
* `alg`: A list of algorithm references from the JW* family of tokens (defined in [[spec:RFC7518]] [Section 3](https://datatracker.ietf.org/doc/html/rfc7518#section-3).) that may be supported within the format. 
* `proof_type`: A list of Linked-Data integrity proof types (defined in the [[ref:Data-Integrity]] draft specification, a work item of the Verifiable Credentials working group at the W3C) that may be supported within the format.

### Additional Instructions for Registrants

Please mention in PR commentary the implementers using the claim format being added and a rationale for the abbreviations and `alg`/`proof_type` naming conventions used.

### Conditions for Rejection or Removal

Maintainers reserve the right to reject, remove, or delay acceptance of PRs. 

## Registry 

|Abbrev|AKA|Description|`alg`|`proof_type`|
|---|---|---|---|---|
|`jwt`|"Vanilla JWT"|The format is a JSON Web Token (JWT) as defined by [[spec:RFC7519]] that will be submitted in the form of a JWT encoded string. Expression of supported algorithms in relation to this format MUST be conveyed using an alg property paired with values that are identifiers from the JSON Web Algorithms registry [[spec:RFC7518]].|See [[spec:RFC7518]] [Section 3](https://datatracker.ietf.org/doc/html/rfc7518#section-3).|n/a|
|`jwt_vc`,`jwt_vp`|"JWT VC/VP"|These formats are JSON Web Tokens (JWTs) [[spec:RFC7519]] that will be submitted in the form of a JWT-encoded string, with a payload extractable from it defined according to the JSON Web Token (JWT) [section] of the W3C [[ref:VC-DATA-MODEL]] specification. Expression of supported algorithms in relation to these formats MUST be conveyed using an JWT `alg` property paired with values that are identifiers from the JSON Web Algorithms registry in [[spec:RFC7518]] [Section 3](https://datatracker.ietf.org/doc/html/rfc7518#section-3).|See [[spec:RFC7518]] [Section 3](https://datatracker.ietf.org/doc/html/rfc7518#section-3).|n/a|
|`ldp`|"Linked Data Proof"|The format is a Linked-Data Proof that will be submitted as an object. Expression of supported algorithms in relation to these formats MUST be conveyed using a `proof_type` property with values that are identifiers from the Linked Data Cryptographic Suite Registry ([[ref:LDP-Registry]]).|n/a|See [[ref:LDP-Registry]]|
|`ldp_vc`, `ldp_vp`|"Linked-Data VC/VP"|Verifiable Credentials or Verifiable Presentations signed with Linked Data Proof formats. These are descriptions of formats normatively defined in the W3C Verifiable Credentials specification [[ref:VC-DATA-MODEL]], and will be submitted in the form of a JSON object. Expression of supported algorithms in relation to these formats MUST be conveyed using a proof_type property paired with values that are identifiers from the Linked Data Cryptographic Suite Registry ([[ref:LDP-Registry]]).|n/a|See [[ref:LDP-Registry]]|
|`ac_vc`|"AnonCreds VC"|This format is for Verifiable Credentials using AnonCreds. AnonCreds is a VC format that adds important privacy-protecting ZKP (zero-knowledge proof) capabilities to the core VC assurances.|See [[ref:AnonCreds]]|n/a|
|`ac_vp`|"AnonCreds VP"|This format is for Verifiable Presentations using AnonCreds. AnonCreds is a VC format that adds important privacy-protecting ZKP (zero-knowledge proof) capabilities to the core VC assurances.|See [[ref:AnonCreds]]|n/a|
|`mso_mdoc`|"mDoc"|The format is defined by ISO/IEC 18013-5:2021 [[ref:ISO.18013-5]] whcih defines a mobile driving license (mDL) Credential in the mobile document (mdoc) format. Although ISO/IEC 18013-5:2021 [[ref:ISO.18013-5]] is specific to mobile driving licenses (mDLs), the Credential format can be utilized with any type of Credential (or mdoc document types).|See [[ref:ISO.18013-5]], [[ref:ISO.18013-7]]|n/a|
|`sd_jwt`|"SD-JWT"|The format is a Selective Disclosure JSON Web Token (SD-JWT). It allows for selective disclosure of claims, meaning that only a subset of the claims contained within the JWT is disclosed during the presentation, enhancing privacy. This is achieved by using cryptographic mechanisms that enable the verifier to confirm the integrity and authenticity of the disclosed claims without needing to see the entire set of claims.|See [[ref:SD-JWT]]|n/a|

## JSON Schemas

[[ref:JSON Schema]]s defined using [JSON Schema Draft 7](https://json-schema.org/specification-links#draft-7).

### Presentation Definition Claim Format Designations

```json
[[insert: ./schemas/presentation-definition-claim-format-designations.json]]
```

### Presentation Submission Claim Format Designations

```json
[[insert: ./schemas/presentation-submission-claim-format-designations.json]]
```

## Appendix

### References

[[def:ISO.18013-5]]
~ [ISO.18013-5](https://www.iso.org/standard/69084.html). ISO/IEC JTC 1/SC 17 Cards and security devices for personal identification, "ISO/IEC 18013-5:2021 Personal identification — ISO-compliant driving license — Part 5: Mobile driving license (mDL) application", 2021.

[[def:ISO.18013-7]]
~ [ISO.18013-7](https://www.iso.org/standard/82772.html). ISO/IEC JTC 1/SC 17 Cards and security devices for personal identification, "ISO/IEC DTS 18013-7 Personal identification — ISO-compliant driving license — Part 7: Mobile driving license (mDL) add-on functions", 2024, <https://www.iso.org/standard/82772.html>.

[[def:VC-DATA-MODEL]]
~ [Verifiable Credentials Data Model v1.1](https://www.w3.org/TR/vc-data-model/). Gregg Kellogg, Pierre-Antoine Champin, Manu Sporny, Grant Noble, Dave Longley, Daniel C. Burnett, Brent Zundel, Kyle Den Hartog. 03 March 2022. Status: W3C Recommendation.

[[def:JSON Schema]]
~ [JSON Schema](https://json-schema.org/). [JSON Schema Draft 7: A Media Type for Describing JSON Documents](https://json-schema.org/draft-07/draft-handrews-json-schema-01). A. Wright, H. Andrews. Status: 20 September 2018. Internet-Draft.

[[def:LDP-Registry]]
~ [LDP-Registry](https://w3c-ccg.github.io/ld-cryptosuite-registry/)

[[def:Linked Data Proofs, Data Integrity]]
~ [Verifiable Credential Data Integrity 1.0](https://www.w3.org/TR/vc-data-integrity/). Securing the Integrity of Verifiable Credential Data. Manu Sporny, Dave Longley, Greg Bernstein, Dmitri Zagidulin, Sebastian Crane. 14 June 2024. Status: W3C Candidate Recommendation Draft.

[[def:AnonCreds]]
~ [AnonCreds v1.0 Draft](https://hyperledger.github.io/anoncreds-spec/). Stephen Curran, Artur Philipp, Hakan Yildiz, Sam Curren, Victom Martinez Jurado, Aritra Bhaduri, Artem Ivanov. Status: v1.0 Draft.

[[def:SD-JWT]]
~ [Selective Disclosure for JWTs (SD-JWT)](https://datatracker.ietf.org/doc/draft-ietf-oauth-selective-disclosure-jwt/). Daniel Fett, Kristina Yasuda, Brian Campbell. Status: Internet-Draft.