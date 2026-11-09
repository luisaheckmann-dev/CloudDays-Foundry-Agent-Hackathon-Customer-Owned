# Customer Administrator: Permissions and Bootstrap

[Home](../README.md) | [From-zero setup](CUSTOMER-SETUP.md) | [Facilitation](FACILITATION.md)

The customer administrator operates **inside the customer's directory and
subscription**. The instructor neither creates customer identities nor
collects participant email lists, passwords, tokens, or MFA codes. Use existing
customer corporate identities and customer-internal groups. Any additional
identity or consent decision belongs to the customer.

## Separate Bootstrap from Building

| Operation | Customer-approved authority | Scope and caveats |
|---|---|---|
| Approve subscription, spending, region, policies and network | Customer subscription/security owners | Organizational approval, not a workshop role |
| Create a dedicated resource group or register providers | Customer subscription administrator with the relevant actions | Foundry project access is insufficient; an RG-scoped role cannot register subscription providers |
| Create Foundry resource/project and deploy/manage model | Foundry Account Owner or other approved resource-management role | Appropriate subscription or dedicated RG scope; Foundry Account Owner alone has no build/run data actions |
| Assign human, managed-identity, storage or monitoring roles | Administrator with `Microsoft.Authorization/roleAssignments/write` for each target | Azure Contributor cannot assign roles; Foundry roles' conditional assignment powers are limited |
| Create/edit/test agents and project vector stores | Participant: Foundry User on their project | Foundry Agent Consumer is insufficient for authoring |
| Navigate parent Foundry resource | Reader on the Foundry resource when needed | No general resource-wide write or project data access implied |
| Access deployed models from the project runtime | Project managed identity with verified Foundry resource/model access | Check actual identity and assignments, not just the human user's roles |
| Upload files through customer storage, where applicable | Storage Blob Data Contributor on the actual project upload storage scope | Only for a verified data path that requires it; no speculative role on unrelated storage |
| View quota/eligibility | Approved customer admin; Cognitive Services Usages Reader if needed | This role must be at **subscription** scope to authorize quota visibility; not routine for all attendees |
| Read approved traces | Approved trace reader; e.g. Log Analytics Reader | Scope to connected monitoring; protected tables/workspace access can require additional approval |

**Foundry User cannot create accounts/projects, manage model deployments, or
assign roles.** Azure Owner/Contributor supplies control-plane permissions,
not Foundry data actions by itself. Foundry Owner combines privileged
management and data capabilities; do not make it the default attendee role.
Do not grant broad Owner, Contributor, Global Administrator, or subscription
Foundry User merely to get a workshop working.

The official [RBAC reference](REFERENCES.md#official-product-guidance) includes
both resource-wide quickstart assignments and project-scoped enterprise
patterns. For multiple participants use project-scoped Foundry User plus
parent Reader, then verify every actual portal operation. If that path
requires an additional permission, investigate the denied action and grant
only the customer-approved targeted permission. Do not silently widen access
to every project in the resource.

## Browser Role Assignment Procedure

1. Sign in to the [Azure portal](https://portal.azure.com) with your own
   authorized customer admin identity. Select the approved directory and
   subscription. Complete any customer-approved privileged-role activation.
2. Open the **specific target resource** and **Access control (IAM)**.
   Use **Check access** to inspect direct and inherited roles.
3. If an assignment is approved, choose **Add > Add role assignment**.
   Select the exact role; read its permissions and intended scope.
4. For a human/group select **User, group, or service principal**. Choose the
   customer-internal principal confirmed by your directory, not a guessed
   name or an instructor identity. Review the target scope, then assign.
5. To grant participant project access, use Foundry **Manage > Project
   details > Users > Add user** when exposed and scoped to the intended
   project; choose **Foundry User**. Alternatively use project-scoped Azure
   IAM if your portal exposes it. Verify the resulting scope. If neither
   browser path can set the correct scope, stop with `BLOCKED` for the
   customer's access administrator; do not introduce a command-line step.
6. On the parent Foundry resource, assign **Reader** for navigation only if
   required by the customer-approved design.
7. For the project runtime select **Managed identity** on the Foundry
   resource's IAM page and select the **project's** managed identity.
   The documented baseline is Foundry User on that Foundry resource for the
   project identity. Verify it against the deployed model and customer policy;
   this is not a reason to grant resource-wide roles to all humans.
8. For Standard setup, apply the current Agent Service documentation's
   resource-specific roles to the correct managed identities and actual
   Storage/Search/Cosmos resources. Human upload rights and runtime rights
   are different. Do not substitute account keys.
9. Review the final assignments, including inherited access. Allow normal
   propagation, refresh the session, and have the participant test using
   **their own** sign-in. Do not test by sharing admin credentials.

In the new Foundry portal a creator who can assign roles may automatically
receive Foundry User on the resource, and the project's managed identity may
receive it too. **Verify both**; creation success is not proof of correct
data access. Review broad inherited creator assignments separately before
claiming participant isolation. A customer admin performing the bootstrap
must not leave the attendee with unnecessary administrator rights.

Role names are being renamed from Azure AI User/Owner/Account Owner to
Foundry User/Owner/Account Owner. If an older label appears, verify its
official role definition and scope; similarly named legacy hub/ML roles are
not interchangeable.

## Provider Registration When Required

1. In Azure portal open **Subscriptions > your customer subscription >
   Resource providers**.
2. Inspect the deployment error and planned resource types. Foundry normally
   uses `Microsoft.CognitiveServices`; approved monitoring can also require
   `Microsoft.Insights` and `Microsoft.OperationalInsights`. Standard setups
   may need `Microsoft.Storage`, `Microsoft.Search`, and
   `Microsoft.DocumentDB`, depending on the actual architecture.
3. The customer's subscription administrator registers only required,
   approved providers using **Register**, and waits for **Registered**.
   Do not register every provider or modify policy exemptions indiscriminately.
4. Reopen the failed deployment and reconcile its resources before retrying.
   Provider registration does not grant the caller data-plane permissions,
   waive quota, or bypass Azure Policy.

## Bootstrap Handoff Inside the Customer Organization

Privately record approved directory/subscription, dedicated RG, Foundry
resource/project, model deployment and version/type/region, setup mode,
project identity, role scopes, monitoring decision, cost owner, retention,
and cleanup owner. Use a customer-approved location, **not this repository**.
No keys are required. The instructor needs no identity export or private
resource inventory.

If a participant lacks bootstrap rights, the customer's own administrator
follows [setup sections 1-7](CUSTOMER-SETUP.md) in the customer environment.
The participant still creates the two agents, uploads/indexes documents,
and tests them in the browser. Admin execution is a separation of duties,
not a provider-side preprovisioning fallback.

## Isolation Check

Prefer one person per project. A team may intentionally share one project
only when the customer approves that its agents, files, vector stores,
conversations, and indexes form a common access boundary. Individual agents
are not a confidentiality boundary inside a shared project.

Check project membership and inherited parent/group assignments without
opening another person's data. A participant must be unable to build or
access data in another private project. Mere visibility of a project name
through Reader is not permission to inspect its data. Report unexpected
access to the customer security owner, remove only approved excess grants,
and retest. Never test isolation against an instructor environment.
