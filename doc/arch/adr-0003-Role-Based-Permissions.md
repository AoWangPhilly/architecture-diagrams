# ADR 3: Role-Based Permissions

| Category   | Value            |
| ---------- | ---------------- |
| Identifier | adr-0003         |
| Status     | Accepted         |
| Author(s)  | Ao Wang          |
| Date:      | April 30th, 2024 |

Some data should only be accessible to certain users. For example, a user should only be able to access their own data and not other users' data. However in an organization, there are different roles that have different levels of access to data. For example, a manager may have access to all data, while a regular employee may only have access to their own data. Another example may be a hospital, since patient data is sensitive, only doctors and nurses should have access to patient data. This is crucial for security and privacy reasons as well as for compliance with regulations such as GDPR and HIPAA.

## Decision

We will utilize Okta's role-based access control (RBAC) to control access to data. RBAC will have core elements of administrators, roles, and permissions. Administrators will be able to create roles and assign permissions to roles. Roles will be assigned to users. Permissions will be assigned to roles. This will allow for fine-grained access control to data.

## Rationale

The driving force for influencing this design decision is security and privacy. We need to ensure that data is only accessible to those who are authorized to access it. Additionally, we need to ensure that we are compliant with regulations such as GDPR and HIPAA. Okta's RBAC is a widely used and well-documented solution for role-based access control. On our platform, the consumers are able to create their own roles and assign permissions to those roles, deciding who's able to read and write data.

The main alternative to Okta's RBAC is to build our own role-based access control system. However, this would require a lot of development time and resources. Additionally, Okta's RBAC is a widely used and well-documented solution, which means that it's more likely to be secure and compliant with regulations such as GDPR and HIPAA.

## Consequences

Since we are using a third-party solution, we are dependent on Okta's RBAC. If Okta's RBAC goes down, we will not be able to control access to data. Additionally, we will need to pay for Okta's RBAC, which can lead to higher costs. However, the benefits of using Okta's RBAC far outweigh the downsides, as we're in the business of providing secure and compliant access to data, which is crucial for our platform. This will help save money on development time and resources.
