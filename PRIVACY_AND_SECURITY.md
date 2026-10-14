# Privacy Policy, Data Residency & Terms of Use — JSM Portal Guard

**Effective Date**: October 14, 2026  
**Publisher**: EvidencePair LLC  
**App ID**: `ari:cloud:ecosystem::app/46bde883-178a-469f-8082-e951adb34b9f`

---

## 1. Zero Data Egress & Architecture Statement ("Runs on Atlassian")

**JSM Portal Guard** executes 100% inside Atlassian's managed Forge Cloud runtime (`nodejs24.x`) and declares **zero external remote endpoints (`remotes:`)** and **zero external fetch permissions**.

- **0 Bytes External Storage**: EvidencePair LLC does not operate any external servers, databases, or analytics endpoints that receive customer data from JSM Portal Guard.
- **100% Native Jira Entity Property Storage**:
  - Cascading field rules are stored exclusively inside your Jira instance's **Project Properties** (`/rest/api/3/project/{projectId}/properties/jsmPortalGuardConfig`).
  - Customer portal approval sign-offs and SHA-256 audit hashes are stored exclusively inside your Jira instance's **Issue Properties** (`/rest/api/3/issue/{issueKey}/properties/jsmPortalGuardApproval`).

---

## 2. Data Residency & Compliance Inheritance

Because JSM Portal Guard stores 100% of its configuration and audit data within native Jira Project Properties and Jira Issue Properties:
- **Automatic Data Residency**: All app data automatically resides in the exact geographic region (e.g., US, EU, AU, DE, SG, CA, UK, JP) configured for your host Jira Service Management Cloud product under Atlassian Data Residency.
- **Backup, Restore & Deletion**: App data is automatically included in standard Jira Cloud backups and is permanently purged when the corresponding Jira issue or project is deleted by your organization.

---

## 3. Privacy Policy (GDPR / CCPA / SOC 2 Alignment)

### Personal Data Processed
To provide tamper-evident customer approval attribution, JSM Portal Guard processes:
- **Atlassian Account ID (`accountId`)** of the portal customer or project administrator performing an action.
- **Approval Timestamp (`ISO-8601 UTC`)**, **Decision (`APPROVED` / `REJECTED`)**, and optional **Sign-Off Comment** submitted on the JSM ticket.

### How Personal Data Is Used
- Processed solely within the Atlassian Forge runtime to compute a deterministic SHA-256 integrity digest (`accountId|issueKey|timestamp|decision`) and display the verification badge inside the Jira Service Management request view.
- Never transmitted outside your Atlassian Cloud tenant, never sold, and never shared with third parties.

### Data Subject Rights (Access, Rectification, Erasure)
Organization administrators have full read/write/delete control over all JSM Portal Guard records at any time via standard Jira REST v3 APIs:
- `GET` / `DELETE /rest/api/3/project/{projectIdOrKey}/properties/jsmPortalGuardConfig`
- `GET` / `DELETE /rest/api/3/issue/{issueKey}/properties/jsmPortalGuardApproval`

---

## 4. Terms of Use & End-User License Agreement (EULA)

1. **License Grant**: Subject to an active Atlassian Marketplace subscription or evaluation license, EvidencePair LLC grants Customer a non-exclusive, non-transferable license to use JSM Portal Guard on Customer's subscribed Atlassian Cloud site.
2. **Customer Responsibility**: Customer is responsible for configuring project rules and verifying that workflow configurations meet Customer's internal compliance policies.
3. **Warranty & Liability**: JSM Portal Guard is provided via the Atlassian Marketplace "AS IS" under the standard Atlassian Marketplace Partner Agreement. In no event shall EvidencePair LLC's aggregate liability exceed the fees paid by Customer for the App during the twelve (12) months preceding the claim.
4. **Support & Contact**: Technical support and security inquiries may be submitted to `support@titlecovenant.com`.
