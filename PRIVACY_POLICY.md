# Privacy policy: Portal Forms and Approvals for Jira Service Management

Updated 9 November 2026

This policy describes the Atlassian Marketplace app **Portal Forms and Approvals for Jira Service Management** ("the app"), made by EvidencePair LLC ("EvidencePair", "we"). EvidencePair's company privacy policy, which covers our website and email you send us, is at <https://evidencepair.com/privacy/>.

## In short

- The app runs on Atlassian Forge, inside your Jira site. It declares no external egress and no remote services, and it makes requests only to your site's Jira APIs.
- It keeps its data in Jira itself: a project property for each project that uses it, an issue property for each request with a decision, and a Jira UI modification. That data is never sent to EvidencePair.
- The only personal data it stores itself is the Atlassian account ID of the person who records an approval decision, the account ID of the person whose action last saved the field rules, and whatever people type into a decision's comment or a rule.
- Its entries in the Forge platform's logs include the account ID of each person who opens the approval panel.

## What the app stores

**One project property, `jsmPortalGuardConfig`, per project where the field rules have been saved:**

- the field rules. For each rule: its name as typed, the request type, the field that triggers it, the condition and the value it compares against as typed, the field it controls, the action (show and require, show as optional, or hide), and whether it is on;
- the ID of the app's UI modification;
- the Atlassian account ID of the person whose action last saved the property, and when;
- a portal ID, project ID and project key copied from the app's built-in configuration (portal 1, project ID 10035, key ITH). They are the same on every site and do not describe your project.

The app saves this property, and updates its UI modification, when someone saves rules on its project page. It also does both when someone opens the project page or the approval panel and the app finds no UI modification ID stored. In those cases it uses the stored rules or, if there are none, three example rules built into it. The approval panel looks only at the project with ID 10035 from the app's built-in configuration. If that project has no stored UI modification ID, opening the panel updates the UI modification with those rules, and saves them to that project, if your site has one, with the account ID of the person who opened the panel.

**One issue property, `jsmPortalGuardApproval`, per request with a recorded decision:**

- the issue key;
- the Atlassian account ID of the person who recorded the decision;
- the decision: approved or rejected;
- the comment they typed, if any;
- when the decision was recorded;
- a SHA-256 checksum of the account ID, issue key, time and decision, with the algorithm's name and the list of fields it covers. The checksum adds no information of its own. It does not cover the comment.

Each new decision on a request replaces the one before, so only the latest is kept. If Jira supplies no account ID, the app records a fixed account ID from its built-in configuration instead: an administrator account on EvidencePair's own test site.

**A Jira UI modification, which the app creates and then updates:**

- a copy of the field rules, with the same fixed portal ID, project ID and project key, and when it was last updated;
- the portal and request types it applies to: portal 1, request types 1, 6 and 8, and any other request type a rule names;
- a fixed name and description.

If updating the UI modification fails, the app creates a new one.

The app does not look up names, email addresses or profiles. Comments and rule text can contain personal data, and the app stores them as typed.

## What the app reads from Jira

- The project or request the app is opened from, and the account ID of the person using it, from Forge.
- The two properties above. The project page reads its own project's property. The approval panel reads its request's issue property and the property of the project with ID 10035.
- The app's own UI modifications.
- On the portal's request form, the app's script reads the values of the fields its rules depend on while the customer fills in the form, to decide which fields to show or require. Those values stay in the customer's browser. The script stores nothing and sends nothing.

Apart from those form values, it reads no issue fields, comments or attachments.

## Where the data lives

Entity properties are part of your Jira site's data. Atlassian stores them with the rest of your site, in your site's data residency location, under Atlassian's own security and privacy commitments. Jira also keeps the app's UI modification on your site. The app has no storage of its own: it uses no Forge storage and no Forge SQL, and EvidencePair runs no servers in its path.

## Who can see it

Jira shows an entity property to anyone who can view the issue or project it belongs to, through Jira's REST API. That includes the account IDs stored with the field rules and with a decision.

The approval panel shows the latest decision on a request, with its account ID, time, comment and checksum, to anyone who can open that request. If Jira refuses to let that person read the issue property, the app reads it with its own access.

Jira passes the UI modification, rules included, to the app's script on each request form it applies to. The rules therefore reach the browser of anyone who opens one of those forms.

Jira's permissions normally decide who can change the properties: changing an issue property needs permission to edit the issue, and changing a project property needs permission to administer the project. The app first saves as the person using it. If Jira refuses, the app saves with its own access instead. So anyone who can open the app's project page can save field rules, and anyone who can open the approval panel can record a decision.

## Retention and deletion

The app keeps both properties and its UI modification until someone deletes them. It has no retention setting, deletes nothing on its own schedule, and has no uninstall step. Deleting an issue deletes its properties. A Jira administrator can delete either property at any time through Jira's REST API, and should do so before uninstalling if the data must go. The app never deletes its UI modification. Deleting every rule on the project page saves an empty rule list to the project property and the UI modification. Opening the approval panel can then put the example rules back into the UI modification, as described above.

## Account closure

The app does not take part in Atlassian's personal data reporting. When an Atlassian account is closed, its account ID stays in any decision that person recorded, and in the field rules property if that person last saved it, until that property, or the issue, is deleted.

## Platform logs

The app writes these entries to the Forge platform's logs:

- when the project page opens: the project key, the number of rules and the UI modification ID;
- when field rules are saved: whether the save worked, the number of rules, whether the UI modification was updated, and its ID;
- when the approval panel opens: the issue key, the Atlassian account ID of the person who opened it, whether a decision exists, and the UI modification ID;
- when a decision is recorded: the issue key, the decision, the first 12 characters of the checksum, and whether the checksum matched;
- a warning with the error message when an attempt to create or update the UI modification raises an error, or when the approval panel's check of the rules and the UI modification raises one.

The app puts no comments or rule text into these entries. Atlassian keeps these logs under its own policies, and they can be available to EvidencePair as the app's developer. Atlassian's platform can also record errors it sees while the app runs, such as an unhandled error and its message ([Atlassian: view app logs](https://developer.atlassian.com/platform/forge/view-app-logs/)).

## Email and support

If you email us, our [company privacy policy](https://evidencepair.com/privacy/) describes how we handle that email, and the current restrictions on where our apps may be used.

## What we never do

We do not sell personal data or use it for unrelated advertising or AI training. The data the app stores stays in your Jira site, and EvidencePair keeps no copy of it.

## Changes to this policy

The date at the top changes when this policy does. Every version is kept in this repository's history.

## Contact

hello@evidencepair.com
