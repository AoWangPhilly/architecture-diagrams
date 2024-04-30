# ADR 3: Role-Based Permissions

| Category   | Value            |
| ---------- | ---------------- |
| Identifier | adr-0003         |
| Status     | Accepted         |
| Author(s)  | Ao Wang          |
| Date:      | April 30th, 2024 |

Some data should only be accessible to certain users. For example, a user should only be able to access their own data and not other users' data. However in an organization, there are different roles that have different levels of access to data. For example, a manager may have access to all data, while a regular employee may only have access to their own data. Another example may be a hospital, since patient data is sensitive, only doctors and nurses should have access to patient data. This is crucial for security and privacy reasons as well as for compliance with regulations such as GDPR and HIPAA.

## Decision

We will implement role-based permissions to control access to data. We will use a role-based access control (RBAC) model, which is a policy-neutral access control mechanism defined around roles and privileges. The components of RBAC such as role-permissions, user-role, and role-role relationships will be used to control access to data. We will use a role-based permissions system to control access to data based on the user's role.

Describe here our response to these forces, that is, the design decision that was made. State the decision in full sentences, with active voice ("We will...").

## Rationale

Describe here the rationale for the design decision. Also indicate the rationale for significant _rejected_ alternatives. This section may also indicate assumptions, constraints, requirements, and results of evaluations and experiments.

## Status

[Proposed | Accepted | Deprecated | Superseded]
If deprecated, indicate why. If superseded, include a link to the new ADR.

## Consequences

Describe here the resulting context, after applying the decision. All consequences should be listed, not just the "positive" ones.
