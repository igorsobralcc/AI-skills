---
name: authentication-authorization-design
description: Design identity, credentials, sessions, tokens, permissions, resource authorization, rotation, and audit boundaries for applications and APIs.
---

# Authentication and Authorization Design

## Golden rules

- Authentication establishes identity; authorization is evaluated for the requested action and resource.
- Deny by default, grant least privilege, validate issuer, audience, lifetime, signature, and relevant claims, and design credential rotation.
- Centralize policy semantics while keeping resource ownership checks close to authoritative data.
- Make sensitive administrative actions auditable without logging credentials or private payloads.

## Guardrails

- Do not invent cryptographic protocols, store passwords reversibly, trust client-supplied roles, conflate roles with ownership, or leak private resource existence.
- Do not choose an identity provider without requirements and explicit user direction.
- Authentication design does not authorize configuring a live provider.
