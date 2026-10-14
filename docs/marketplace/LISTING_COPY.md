# Atlassian Marketplace Partner Listing Copy — JSM Portal Guard

## App Identity
- **App Name**: JSM Portal Guard — Dynamic Cascading Fields & Tamper-Evident Customer Approvals
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

**JSM Portal Guard** brings two mission-critical capabilities natively to Jira Service Management Cloud—built 100% on Atlassian Forge (`nodejs24.x`) with **zero external servers** and **zero data egress**:

1. **Dynamic JSM Customer Portal Cascading Fields (`JSMRequestCreate`)**:
   - Configure parent-child field visibility, required states, and option filtering per JSM Request Type using the **Portal Guard Rules** Project Admin builder.
   - Powered natively by `@forge/jira-bridge` (`uiModificationsApi`) on `JSMRequestCreate`.
   - **Built-In Validation Safety Rule**: Automatically clears `required` flags (`setRequired(false)`) whenever a dependent field is hidden (`setVisible(false)`), eliminating "ghost required field" submission failures on the customer portal.

2. **21 CFR Part 11-Style Tamper-Evident Customer Portal Approvals (`portalRequestDetailPanel`)**:
   - Empower unlicensed JSM portal customers (`unlicensedAccess: [customer]`) to formally **Approve** or **Reject** requests directly from the Customer Portal ticket view.
   - Generates a deterministic **SHA-256 cryptographic signature** (`accountId|issueKey|timestamp|decision`) for every sign-off and verifies record integrity in real time (`SHA-256 VERIFIED` vs. `TAMPER DETECTED`).
   - Full customer attribution via Forge impersonation (`write:jira-work` with `allowImpersonation: true`).

---

## Why Enterprise & Regulated Teams Choose JSM Portal Guard

- **100% Runs on Atlassian (Zero Data Egress)**:
  - Zero `remotes:`, zero external APIs, and zero third-party databases. All rule configurations are stored in native **Jira Project Properties** (`jsmPortalGuardConfig`), and all customer approval audit trails are stored in native **Jira Issue Properties** (`jsmPortalGuardApproval`).
- **Connect-to-Forge Migration Ready**:
  - Purpose-built on UI Kit 2 (`@forge/react`) and Forge `nodejs24.x` runtime, eliminating legacy Connect iframe vulnerabilities and external data residency headaches.
- **Instant Setup in Under 2 Minutes**:
  - Open **Project Settings -> Portal Guard Rules**, define your trigger conditions for any JSM Request Type, and click **Sync UIM Contexts Now**.

---

## Key Features Checklist
- [x] Dynamic parent-child field show/hide & required toggling on `JSMRequestCreate`
- [x] Automatic hidden-field `setRequired(false)` validation guard
- [x] Unlicensed JSM customer sign-off panel on Portal Request Detail views
- [x] Deterministic SHA-256 cryptographic signature & real-time tamper detection
- [x] 100% Host Entity Property persistence (automatic Atlassian Data Residency inheritance)
