# Customer Billing, Privacy, Retention and Cleanup

[Home](../README.md) | [Setup](CUSTOMER-SETUP.md) | [Admin](ADMIN.md)

All Azure charges belong to the **customer's billing account/subscription**.
The instructor supplies no free or shared hosted capacity. This repository
does not purchase, deploy, delete, schedule expiry, or enforce a spending cap.

## Before Creating Anything

1. Obtain the customer's budget and billing-owner approval. Use the current
   [official pricing references](REFERENCES.md#official-product-guidance),
   region, actual model offer and deployment type; no fixed price is promised.
2. Estimate model input/output tokens, File Search ingestion/storage and
   applicable tool charges, monitoring ingestion/retention, and any Standard
   Storage/Search/Cosmos/network costs. Optional challenge stores and repeated
   tests add usage.
3. Review pay-as-you-go versus provisioned/reserved capacity. A deployment
   with no active chat can still incur charges under its offer; Standard
   backing services and monitoring can remain billable while idle.
4. In Azure portal open the approved scope's **Cost Management > Budgets >
   Add** when your subscription type/permissions support it. Choose the
   customer-approved amount, period, alert thresholds and customer recipients;
   review then create. Use customer tags/resource-group scope as appropriate.
5. Agree who checks actual usage and acts on alerts. **A budget alert is
   not a hard cap or automatic shutdown.** Cost data can be delayed.
6. Record the customer cleanup owner and date before the workshop.

## Retention and Privacy

- Upload only the four synthetic core texts. The optional attack text goes
  only in its separately approved test store. Do not upload customer records,
  credentials, identity exports, internal policies, or account screenshots.
- Conversation history, prompts, model output, file contents, vectors,
  trace spans and diagnostic logs can persist independently. Approve access,
  data location and retention for each according to customer policy.
- Basic setup uses service-managed backing storage for the customer's
  project; it is not equivalent to Standard storage in customer-provisioned
  resources. Choose the [appropriate environment](CUSTOMER-SETUP.md#3-choose-the-agent-environment).
- Inspect the **actual** store expiry setting and lifecycle in your chosen
  setup. There is no assumed seven-day auto-expiry. If the UI does not
  reveal it, ask the customer's service owner; record the uncertainty and
  arrange explicit cleanup. Expiry is not proof every source file, chat
  or trace is deleted.
- Server-side tracing can be enabled by connecting Application Insights.
  Follow customer consent, content-capture and access policy; telemetry may
  contain questions, replies and retrieved passages. Log Analytics retention
  and billing are separate from agent/store deletion.
- Keep evidence notes in an approved private customer location. Public
  sharing requires sanitization and customer approval. Do not commit notes,
  private URLs, screenshots or raw traces to this materials repository.

## Inventory Before Cleanup

Record in a **private customer note**:

```text
Customer scope and approval reference:
Cleanup owner and approved date:
Dedicated RG and resources confirmed workshop-only: yes/no
Agents and all saved versions:
Core store and four source files:
Optional challenge agent/store/five source files:
Other test copies, conversations and attachments:
Model deployment and actual billing offer:
Toolboxes/connections created solely for this workshop:
Application Insights / Log Analytics and retention:
Standard Storage / Search / Cosmos / network dependencies, if any:
Workshop-specific role assignments:
Dependencies outside the proposed deletion scope:
Approved deletion list or approved dedicated RG:
Deletion verification and later cost review:
```

The public example names are not a deletion inventory. Verify actual
ownership, dependencies and shared use for every item.

## Authorized Cleanup in the Browser

**Deletion is destructive. Obtain the customer's explicit approval of the
exact deletion list/scope first.** Do not delete production resources,
shared deployments, ordinary corporate identities or unrelated role grants.

### Route A: Delete a Truly Dedicated Workshop Resource Group

1. In Azure portal select the correct customer directory and subscription.
2. Open the **actual new dedicated workshop RG**. Enumerate its contents,
   deployments, locks, and dependencies. Confirm every resource is exclusively
   workshop-owned and no production/customer service depends on it.
3. Identify workshop artifacts outside that RG: model deployments in other
   resources, shared monitoring workspaces, Standard dependencies, retained
   conversations or data. The RG delete operation does not clean those
   automatically.
4. Review the list with the customer owner. If exclusive ownership is not
   certain, **do not delete the RG**; use Route B or ask the customer owner.
5. After explicit approval, choose **Delete resource group**, confirm the
   exact RG name as the portal requires, and submit. Do not bypass locks or
   policy; the customer owner decides any required authorized change.
6. Wait for completion, refresh the resource list and verify the intended
   resources are gone. Reconcile failure/partial deletion rather than
   submitting repeated destructive requests.
7. Separately handle approved external retention/dependencies and review
   subsequent cost data for remaining charges.

### Route B: Remove Only Individually Approved Workshop Artifacts

1. Verify the customer project and artifact names from your private inventory.
   Stop new test requests and coordinate with any approved team members.
2. In Foundry remove the workshop agents and their saved versions using the
   current portal delete controls. Remove optional challenge copies too.
   Check for versions/publications or references that prevent deletion.
3. Inspect the project's file/vector-store management. Explicitly delete
   approved core/challenge stores **and** approved underlying uploaded files,
   not just the agent attachment. Removing an agent or detaching File Search
   does not necessarily remove the store or files. Verify references first.
4. Remove approved workshop conversations/attachments and any solely
   workshop-owned toolboxes/connections. A fresh chat or closing a tab does
   not delete history. Preserve only customer-approved evidence.
5. The customer model operator deletes the workshop-only model deployment
   if no other application depends on it, or manages its billing commitment
   under the actual offer. Do not assume no traffic means no charges.
6. The customer owner handles workshop-only Standard backing resources,
   monitoring/log workspace resources, networking and diagnostics, after
   checking for shared dependencies and retention obligations. Deleting a
   project does not guarantee every connected resource is deleted.
7. Remove only approved workshop-specific access assignments after any
   necessary verification. Do not disable people's corporate accounts or
   remove non-workshop access.
8. Verify each approved item is absent or has an explicitly documented
   retention/deletion exception, and review costs again after reporting delay.

If your current portal cannot delete a particular artifact, record
**cleanup BLOCKED** and assign it to the customer's service administrator
using an approved browser-supported control path or customer support.
Do not silently introduce SDK/CLI cleanup as a workshop prerequisite,
or claim deletion succeeded when only an attachment disappeared.

**Closing the browser is not cleanup.** Residual charges or data retention
remain the customer's responsibility until the approved lifecycle is verified.
