---
title: "Personal Assertion Token (PASSporT) Extension for AI Usage Preferences in SIP Calls"
abbrev: "AI Preferences in SIP PASSporT"
category: info

docname: draft-altanai-sip-passport-aipref-latest
submissiontype: IETF
number:
date:
consensus: false
v: 3
area: art
workgroup: STIR
keyword:
 - SIP
 - PASSporT
 - AI preferences
 - call data
venue:
  group: stir
  type: Working Group
  mail: stir@ietf.org
  arch: https://mailarchive.ietf.org/arch/browse/stir/
  github: altanai/draft-sip-passport-aipref
  latest: https://altanai.github.io/draft-sip-passport-aipref/draft-altanai-sip-passport-aipref.html

author:
 -
    fullname: Altanai Bisht
    organization: Cisco Meraki
    email: altanai@outlook.com

normative:
  RFC3261:
  RFC8224:
  RFC8225:

informative:
  RFC8946:
  RFC9795:
  I-D.ietf-aipref-vocab:
  I-D.altanai-aipref-realtime-protocol-bindings:

...

--- abstract

This document outlines a potential Personal Assertion Token (PASSporT)
extension for conveying AI usage preferences associated with SIP calls,
including preferences concerning the use of call data for training large
language models (LLMs). It explores binding preference information to
authenticated call identity. This initial discussion outline leaves the
extension design and verification procedures to be determined (TBD).

--- middle

# Introduction {#intro}

PASSporT {{RFC8225}} and the STIR authentication procedures for SIP
{{RFC8224}} provide a basis for associating signed information with calls.
This document explores applying that model to AI usage preferences for
call data. The proposed extension is outlined in {{extension}}, with
SIP procedures reserved in {{sip}}.

TBD: Refine the problem statement, intended status, and initial use cases
with contributors.

## Relationship to Existing Work {#related-work}

AI Preferences for Real-Time Protocol Bindings
{{I-D.altanai-aipref-realtime-protocol-bindings}} describes AI Preference
Tokens (APTs), the SIP `AI-Pref` header field, SDP bindings, and preference
updates during a session. This document explores a specific PASSporT
binding that could complement those mechanisms and the AIPREF vocabulary
{{I-D.ietf-aipref-vocab}}.

The extension structure follows the precedents in {{RFC8946}} and
{{RFC9795}}: claim definitions, SIP authentication and verification
procedures, and separate IANA registration considerations.

TBD: Agree on the boundary between the existing real-time bindings and
this extension, including which mechanisms are reused.

# Terminology {#terminology}

{::boilerplate bcp14-tagged}

TBD: Define preference originator, preference authority, and APT usage
in this document, reusing existing SIP and STIR terminology.

# Overview of Operation {#overview}

TBD: Describe preference expression for call data used in LLM training,
the parties that attach and sign it, and how a receiver obtains and
evaluates the applicable preferences.

# PASSporT Extension {#extension}

## PASSporT Type and Claim Definitions {#claims}

TBD: Define the claim names, syntax, and semantics, and determine whether
a dedicated `ppt` value or a claims-only profile is appropriate under
{{Section 8 of RFC8225}}. No new claim or type name is allocated by
this outline.

## Preference Integrity and Call Binding {#integrity}

TBD: Define inline or referenced preference objects, digest inputs,
scope, and version binding. Distinguish the call signer's assertion
from the preference issuer's authority over the affected data.

## Examples {#examples}

TBD: Add complete PASSporT and SIP examples after the claim definitions
and integrity rules are agreed.

# Use in SIP {#sip}

The following sections reserve the SIP {{RFC3261}} procedures for
authentication and verification services, following {{RFC8946}} and
{{RFC9795}}.

## Authentication Service Behavior {#authentication-service}

TBD: Define signer eligibility, PASSporT construction, preference
attachment, and carriage in the SIP `Identity` header field.

## Verification Service Behavior {#verification-service}

TBD: Define signature and credential validation, preference retrieval,
binding checks, and handling of unsupported, unavailable, or invalid
preference information. Distinguish call identity verification from
preference acceptance and enforcement.

# Preference Updates and Call Transitions {#updates}

TBD: Specify applicability to mid-dialog updates, agent-to-human
handoffs, and forwarded or transferred calls, including the relationship
to {{RFC8946}}. Define freshness, ordering, and supersession without
treating an actor change as an automatic change to data-use preferences.

# IANA Considerations {#iana}

TBD: Determine the registrations required by {{claims}}. This outline
does not request allocation of concrete names or values.

## JSON Web Token Claims {#iana-jwt}

TBD: Complete the JWT claim registration template for each new claim,
including its name, description, change controller, and specification
reference, following the precedents in {{RFC8946}} and {{RFC9795}}.

## Personal Assertion Token (PASSporT) Extensions {#iana-passport}

TBD: If a new PASSporT type is selected, provide its `ppt` value and
specification reference for the PASSporT Extensions registry.

# Privacy Considerations {#privacy}

TBD: Address preference disclosure, per-participant scope, access to
referenced objects, and retention of preference evidence with call data.

# Security Considerations {#security}

TBD: Address issuer authority, participant consent, replay, downgrade
and stripping attacks, unauthorized preference changes, and integrity
of referenced objects. A signature alone does not establish user consent
or prove that a recipient followed the expressed preferences.

--- back

# Acknowledgments {#acknowledgments}
{:numbered="false"}

The author thanks Jon Peterson for suggesting exploration of a PASSporT
extension for AI usage preferences associated with call data used in
LLM training.

TBD: Additional acknowledgments.
