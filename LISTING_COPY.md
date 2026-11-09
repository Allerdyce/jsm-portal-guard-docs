# Atlassian Marketplace Partner Listing Copy — Portal Forms and Approvals for Jira Service Management

## App Identity
- **App Name**: Portal Forms and Approvals for Jira Service Management
- **App ID**: `ari:cloud:ecosystem::app/46bde883-178a-469f-8082-e951adb34b9f`
- **Vendor**: EvidencePair LLC
- **Category**: IT & Helpdesk / Workflow & Approvals / Security & Compliance
- **Runs on Atlassian Badge Eligibility**: **100% Eligible** (Native Forge `nodejs24.x`, Zero Remotes, Zero Data Egress)

---

## 80-Character Tagline / Summary
> Dynamic JSM portal cascading fields & SHA-256 customer approval sign-offs.
*(74 characters)*

---

## Full Marketplace Description

### Stop Portal Form Chaos & Unverified Customer Sign-Offs in Jira Service Management

**Portal Forms and Approvals for Jira Service Management** brings two mission-critical capabilities natively to Jira Service Management Cloud—built 100% on Atlassian Forge (`nodejs24.x`) with **zero external servers** and **zero data egress**:

1. **Dynamic JSM Customer Portal Cascading Fields (`JSMRequestCreate`)**:
   - Configure parent-child field visibility and required states per JSM Request Type using the **Portal Forms and Approvals for Jira Service Management** Project Admin builder.
   - Powered natively by `@forge/jira-bridge` (`uiModificationsApi`) on `JSMRequestCreate`.
   - **Built-In Validation Safety Rule**: Automatically clears `required` flags (`setRequired(false)`) whenever a dependent field is hidden (`setVisible(false)`), eliminating "ghost required field" submission failures on the customer portal.

2. **Tamper-Evident Customer Portal Approvals (`portalRequestDetailPanel`)**:
   - Empower unlicensed JSM portal customers (`unlicensedAccess: [customer]`) to formally **Approve** or **Reject** requests directly from the Customer Portal ticket view.
   - Generates a deterministic **SHA-256 checksum** (`accountId|issueKey|timestamp|decision`) for every sign-off and checks it each time the panel loads (`SHA-256 VERIFIED` vs. `TAMPER DETECTED`).
   - Customer attribution: each record holds the customer's account ID, and the app writes it as that customer via Forge impersonation (`write:jira-work` with `allowImpersonation: true`), or with its own access if Jira refuses.

---

## Why Teams Choose Portal Forms and Approvals for Jira Service Management

- **100% Runs on Atlassian (Zero Data Egress)**:
  - Zero `remotes:`, zero external APIs, and zero third-party databases. All rule configurations are stored in native **Jira Project Properties** (`jsmPortalGuardConfig`) and applied through the app's Jira UI modification, and all customer approval audit trails are stored in native **Jira Issue Properties** (`jsmPortalGuardApproval`).
- **Built on Forge**:
  - Purpose-built on UI Kit 2 (`@forge/react`) and the Forge `nodejs24.x` runtime, with no external servers.
- **Quick Setup**:
  - Open **Portal Forms and Approvals for Jira Service Management** in the project sidebar, define your trigger conditions for a JSM Request Type, and click **Add Rule & Sync UI Modifications**.

---

## Key Features Checklist
- [x] Dynamic parent-child field show/hide & required toggling on `JSMRequestCreate`
- [x] Automatic hidden-field `setRequired(false)` validation guard
- [x] Unlicensed JSM customer sign-off panel on Portal Request Detail views
- [x] Deterministic SHA-256 checksum & tamper detection each time the panel loads
- [x] 100% Host Entity Property persistence (stored with your Jira site's data, in its data residency location)
