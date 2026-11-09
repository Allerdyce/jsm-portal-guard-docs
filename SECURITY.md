# Security: Portal Forms and Approvals for Jira Service Management

Updated 9 November 2026

How the Atlassian Marketplace app **Portal Forms and Approvals for Jira Service Management**, made by EvidencePair LLC, handles data, what protects it, how we handle vulnerabilities, and which certifications apply.

## Data handling

- **Forge only.** The app runs on Atlassian Forge (`nodejs24.x`) on Atlassian infrastructure. Atlassian lists it as eligible for the Runs on Atlassian program.
- **No egress.** The manifest declares no external permissions and no remote services. The app makes requests only to your site's Jira APIs, and it loads no analytics, error-reporting services or external assets.
- **No storage of its own.** The app keeps its data in Jira itself, and EvidencePair has no copy. It uses no Forge storage or Forge SQL.
  - The project property `jsmPortalGuardConfig` holds the project's field rules: which request-form fields show, hide or become required for each request type.
  - The issue property `jsmPortalGuardApproval` holds a customer's approval decision: the issue key, the customer's Atlassian account ID, approve or reject, any comment they typed, the time, and a SHA-256 checksum.
  - A Jira UI modification, created and updated by the app, applies the field rules on the customer portal.
- **Who the requests run as.** The app's screens call Jira as the person using them, so Jira applies that person's own permissions. A customer's decision is written as that customer (the `write:jira-work` scope allows the app to act as them). Saving the field rules and recording a decision fall back to the app's own access if the user's request is refused.
- **Logs.** When updating its UI modification fails, the app writes a warning with the error message to Forge's platform logs. It writes no other logs.
- **Permissions it asks for.**
  - `read:jira-work`: read the two properties, and list, create and update the app's UI modification.
  - `write:jira-work`: save a customer's decision to the issue property, as that customer.
  - `manage:jira-project`: save the project's field rules.
  - `read:app-data:jira`, `write:app-data:jira`: declared but not used by this version.
- **What the checksum is.** Each decision carries a SHA-256 checksum of the account ID, issue key, time and decision. It shows whether the stored record still matches what was recorded. It is not a digital signature: someone with permission to edit the issue property could change the record and recompute the checksum.

## Encryption

The app stores nothing outside your Jira site and sends nothing outside Atlassian's platform. Encryption in transit and at rest is provided by Atlassian as part of your site, as described in the [Atlassian Trust Center](https://www.atlassian.com/trust). The app adds no encryption of its own.

## Vulnerability management

- **Reporting.** Email security@evidencepair.com. Tell us the app, what you found and how to reproduce it. Please do not test against sites you do not own. We acknowledge every report within one business day.
- **Response.** EvidencePair adopted a written security incident response plan on 12 October 2026. It covers triage, containment, investigation, notification of Atlassian and affected customers, and recovery.
- **Dependencies.** The app's npm dependencies are pinned in its lockfile. Atlassian maintains and patches the Forge runtime.
- **Bug bounty.** We do not run a bug bounty programme.

## Certifications

EvidencePair holds no security certifications, and the app has had no independent penetration test or external audit. The infrastructure the app runs on is Atlassian's, and Atlassian's own certifications cover it: see the [Atlassian Trust Center](https://www.atlassian.com/trust).
