# Privacy, Data Residency & Terms of Use — Portal Forms and Approvals for Jira Service Management

> The app's privacy policy is [PRIVACY_POLICY.md](./PRIVACY_POLICY.md). Its security documentation (data handling, encryption, vulnerability management and certifications) is [SECURITY.md](./SECURITY.md). This page is a short summary of both.

**Effective Date**: October 14, 2026  
**Updated**: 9 November 2026  
**Publisher**: EvidencePair LLC  
**App ID**: `ari:cloud:ecosystem::app/46bde883-178a-469f-8082-e951adb34b9f`

---

## 1. Zero Data Egress & Architecture Statement ("Runs on Atlassian")

**Portal Forms and Approvals for Jira Service Management** executes 100% inside Atlassian's managed Forge Cloud runtime (`nodejs24.x`) and declares **zero external remote endpoints (`remotes:`)** and **zero external fetch permissions**.

- **0 Bytes External Storage**: EvidencePair LLC does not operate any external servers, databases, or analytics endpoints that receive customer data from Portal Forms and Approvals for Jira Service Management.
- **Native Jira Storage**:
  - Cascading field rules are stored inside your Jira instance's **Project Properties** (`/rest/api/3/project/{projectId}/properties/jsmPortalGuardConfig`), with the account ID of the person whose action last saved them. A copy of the rules is kept in the app's Jira UI modification, which applies them on the customer portal.
  - Customer portal approval decisions and their SHA-256 checksums are stored inside your Jira instance's **Issue Properties** (`/rest/api/3/issue/{issueKey}/properties/jsmPortalGuardApproval`).

---

## 2. Data Residency

Jira project and issue properties are part of your Jira site's data. Atlassian stores them with the rest of your site, in your site's data residency location. Deleting an issue deletes its approval record. The app has no retention setting and no uninstall step, and deletes nothing on its own; the [privacy policy](./PRIVACY_POLICY.md) explains how to remove its data.

---

## 3. Privacy Summary

### Personal Data Processed
- **Atlassian Account ID (`accountId`)** of the portal customer who records a decision, and of the person whose action last saved the field rules.
- **Approval Timestamp (`ISO-8601 UTC`)**, **Decision (`APPROVED` / `REJECTED`)**, and optional **Sign-Off Comment** submitted on the JSM ticket.
- The account ID of each person who opens the approval panel is written to Forge's platform logs.

### How Personal Data Is Used
- Processed within the Atlassian Forge runtime to compute a deterministic SHA-256 checksum (`accountId|issueKey|timestamp|decision`) and display the verification badge in the approval panel on the request.
- Never sent outside Atlassian's platform, never sold, and never shared with third parties.

### Access, Correction and Deletion
Jira administrators can read and delete the app's records at any time via standard Jira REST v3 APIs:
- `GET` / `DELETE /rest/api/3/project/{projectIdOrKey}/properties/jsmPortalGuardConfig`
- `GET` / `DELETE /rest/api/3/issue/{issueKey}/properties/jsmPortalGuardApproval`

---

## 4. Terms of Use & End-User License Agreement (EULA)

1. **License Grant**: Subject to an active Atlassian Marketplace subscription or evaluation license, EvidencePair LLC grants Customer a non-exclusive, non-transferable license to use Portal Forms and Approvals for Jira Service Management on Customer's subscribed Atlassian Cloud site.
2. **Customer Responsibility**: Customer is responsible for configuring project rules and verifying that workflow configurations meet Customer's internal compliance policies.
3. **Warranty & Liability**: Portal Forms and Approvals for Jira Service Management is provided via the Atlassian Marketplace "AS IS" under the standard Atlassian Marketplace Partner Agreement. In no event shall EvidencePair LLC's aggregate liability exceed the fees paid by Customer for the App during the twelve (12) months preceding the claim.
4. **Support & Contact**: Technical support: https://evidencepair.com/support/ (support@evidencepair.com). Security issues: `security@evidencepair.com` (see [SECURITY.md](./SECURITY.md)). Privacy: hello@evidencepair.com (see [PRIVACY_POLICY.md](./PRIVACY_POLICY.md)).
