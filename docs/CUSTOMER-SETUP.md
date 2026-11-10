# Customer Setup: Start with Zero Workshop Resources

[Home](../README.md) | [Admin permissions](ADMIN.md) | [Labs](LABS.md) | [Help](TROUBLESHOOTING.md)

**Allow 60-90 minutes or more, plus organizational approval lead time.**
Nothing here is precreated in Azure. The following are browser actions
for an authorized customer operator; this repository does not execute them.
No account keys, terminal, SDK, local application, or hosted function is used.

Complete sections 1-7 as prework where possible. On the workshop day,
facilitators will help participants configure Foundry access in their own
subscriptions with their own Microsoft Entra identities, as far as customer
permissions and prerequisites allow. Start with
[Lab 0](LABS.md#lab-0-configure-and-verify-your-customer-access) for this support.
Bring your own customer sign-in/MFA, an approved active subscription and a
reachable customer administrator. Missing approvals, permissions, quota or
network prerequisites may require a separate setup clinic or follow-up.

Required setup must be ready before Lab 1. During Labs 1-2 follow sections
8-10 to create the learning artifacts. An authorized solo learner may do all
steps. For managed customer environments, the customer's admin performs
bootstrap and grants least-privilege project access; facilitators guide the
steps without taking over credentials or requiring access to the customer's
tenant. The participant does the labs.

## 1. Approve the Customer Environment

1. Agree who owns the customer Azure subscription, spending, and deletion.
   An active Azure subscription is required; access to Microsoft 365 or a
   corporate email account alone is not an Azure entitlement.
2. Ask your customer admin to approve Foundry Agent Service, a model
   compatible with **prompt agents and File Search**, and an eligible region.
   Check [official support and pricing](REFERENCES.md#official-product-guidance).
   No particular model or region is promised in every subscription.
3. Confirm data residency and deployment type. The Foundry resource location,
   model processing geography (regional/data-zone/global), backing storage,
   monitoring workspace, and retention can differ. Do not assume a global
   deployment keeps processing in the resource's region.
4. Approve costs for model tokens or capacity, File Search indexing/storage,
   any applicable tool use, monitoring, and Standard backing resources.
   Define a customer budget alert and a named person who can stop spending.
   An alert is not a hard cap.
5. Confirm customer Azure Policy, permitted model offers, marketplace/terms
   acceptance if applicable, subscription quota, service availability, and
   network/private-endpoint requirements. Only the customer can approve
   consent or purchasing. Do not accept terms on the customer's behalf.
6. Have customer IT permit the approved browser route to GitHub, Azure portal,
   Foundry, Entra sign-in, and necessary customer resource data paths. On a
   private-network setup use an approved network/browser session with correct
   DNS and routing. Do not enable public access just to bypass policy.
7. Confirm browser plain-text download, upload, and clipboard policy. If
   prohibited, ask customer IT for an approved browser file-transfer route.
   If none exists, the full hands-on path is `BLOCKED`.

**Checkpoint:** The customer has approved scope, billing, region, network,
data/trace policy, quota, and an authorized operator. An unresolved approval
is a blocker, not permission to use another organization's resources.

## 2. Sign In and Create a Dedicated Resource Group

1. Open a browser profile approved by your customer. Sign in to the
   [Azure portal](https://portal.azure.com) with your corporate customer
   identity and complete customer MFA/Conditional Access.
2. In the account/directory menu verify the **customer directory**. In
   **Subscriptions**, open the approved active **customer subscription**.
   Have the customer admin confirm the private directory/subscription IDs
   when display names are ambiguous. Do not publish those IDs.
3. Check your roles using the [admin guide](ADMIN.md). Creating resource
   groups and registering providers needs subscription-level authority for
   those actions; Foundry User on a project is not sufficient.
4. If a required provider is unregistered, the customer's admin follows
   [provider registration](ADMIN.md#provider-registration-when-required).
5. Search for **Resource groups**, select **Create**, and select the approved
   subscription explicitly.
6. Enter a new dedicated name, for example `rg-orderops-workshop`. Use a
   customer-chosen suffix if needed. If that name already exists, do not
   reuse it without checking ownership and dependencies.
7. Select the approved resource-group metadata region. This setting does
   not itself select the eventual model-processing or data-storage region.
   Add customer-required owner/purpose/expiry tags without personal data.
8. Select **Review + create**, inspect subscription/name/location, then
   **Create**. Open the resource group and verify its name, subscription,
   tags, and successful creation.

**Checkpoint:** A new, customer-owned workshop-only RG exists. Record it
privately for cleanup. If creation is denied, send the error code and target
scope to your customer admin; do not request blanket attendee Owner access.

## 3. Choose the Agent Environment

**Default learning path: customer-owned Basic/managed Agent Service setup.**
Use it only if your customer accepts service-managed backing storage and
the approved networking and retention model. You still create your own
Foundry resource/project/model. No instructor service is involved.

**Enterprise branch: Standard setup or Standard with private networking.**
If customer policy requires all files, conversations, and vectors in
customer-provisioned resources, Basic is not an equivalent substitute.
Standard can require customer Azure Storage, Azure AI Search, Cosmos DB,
connections, managed-identity roles, networking, DNS, and separate costs.
Follow the [official environment setup and BYO/private-network references](REFERENCES.md#official-product-guidance)
with the customer's architecture/admin team. Use supported browser deployment
forms and approved customer parameters; review every proposed resource,
region, role, network setting, and charge before the customer submits.

This workshop fully describes the Basic browser route. It does **not** claim
every enterprise Standard topology has a universal no-code setup wizard.
If your required Standard architecture cannot be approved and provisioned
through the customer's browser-supported route, mark bootstrap `BLOCKED`.
Do not introduce a hidden template-editing, CLI, SDK, or shared-host fallback.
Resume sections 4-10 only once your own customer environment is ready.

## 4. Create the Foundry Resource and Project

1. Open [Microsoft Foundry](https://ai.azure.com) and verify your customer
   identity and directory again. Enable **New Foundry** if a toggle is shown.
   These instructions target **Foundry (new)**, not a classic hub project.
2. On first use select **Create a new project** in the project picker.
   If a project is already open, select its name at the upper left, then
   **Create new project**. You are creating a new workshop workspace, not
   selecting a sample or another organization's workspace.
3. Enter a new project name, for example `orderops-workshop`.
4. Open **Advanced options** before creating anything. Explicitly select
   the approved **subscription**, the **new dedicated resource group**,
   and approved **location**. Review any automatic defaults.
5. If the form asks for a Foundry resource/account name, choose a new,
   globally unique, customer-owned name such as
   `<customer-chosen-unique-name>`. The angle-bracket text is a placeholder,
   not a literal resource name. Follow the portal's naming validation.
   If a parent-resource selector appears, choose **Create new** for this
   from-zero path; do not accidentally choose a production parent.
6. Some rollouts create the parent Foundry resource automatically with the
   project. If so, inspect the proposed/created parent in the overview and
   Azure resource group. If subscription, parent, or location cannot be
   reviewed, cancel and use the customer's approved Azure portal
   **Create a resource > Microsoft Foundry** form, then create the project
   under that new resource. If the correct new-project route is unavailable,
   stop with `BLOCKED` rather than guessing or switching to classic.
7. Review managed identity and networking options. Keep the approved
   customer Entra/managed-identity design; do not copy keys or add an external
   connection. The resource needs project support and its managed identity;
   verify that the project has its own managed identity after creation.
8. Review all proposed resources and costs, then choose **Create project**
   (or the final create/review action in your form).
9. Wait for project readiness. In Azure portal open the dedicated RG and
   **Deployments**; check the relevant operation shows **Succeeded** and
   that resource/project provisioning has completed. Refresh rather than
   submitting duplicates while deployment is still running.
10. In Foundry **Manage > Project details / Resource details**, confirm the
    intended parent, project, subscription and region; in Azure verify the
    created resources belong to the dedicated workshop scope.

**Checkpoint:** Both new resource and project are ready in the customer
subscription. A project page alone is not proof of the correct billing
scope. Failed deployment: inspect the deployment's error and any partial
resources with the customer admin before retrying.

## 5. Verify Human and Project Identity Permissions

1. Have the customer admin inspect role assignments for the **human** and
   the **project managed identity** separately using [the admin procedure](ADMIN.md#browser-role-assignment-procedure).
2. Confirm participant **Foundry User on this project** and parent
   **Reader** where navigation requires it. This role allows authoring,
   not new accounts, model deployment, or arbitrary role assignment.
3. Verify runtime/model access for the project's managed identity on the
   actual Foundry resource. A role-assignment-capable creator may trigger
   automatic Foundry User assignments to both creator and project identity;
   never assume they exist or have the intended scope.
4. For Standard setup verify exact Storage/Search/Cosmos connections and
   data roles. For file uploads, apply Storage Blob Data Contributor only
   on the actual storage scope when that path requires it.
5. Allow permission propagation and refresh/sign in again as necessary.
   Have the participant open **Build > Agents** with their own identity.
   A successful administrator session does not prove participant access.

**Checkpoint:** The participant can reach the project and create agents;
the project identity can access its approved model/resources. No broad
administrator grants were added merely to clear an error.

## 6. Deploy Your Model

The **customer's authorized model operator** performs this section. Attendees
with only Foundry User do not need or receive model-management rights.

1. In the new project open **Build > Models > Deploy > Deploy a base model**.
   Other rollouts expose the catalog first and a **Deploy** action on a
   model card. Choose the deployment into **your new customer resource**.
2. Use the model catalog and current support tables to choose an available
   text/chat model and version that support **prompt agents and File Search**
   in the approved region/setup. The official resource quickstart illustrates
   `gpt-5-mini`; that is an example, not a guarantee or requirement here.
3. Before confirming, expand configuration/default settings. Review the
   selected subscription/resource, model/version, deployment type, region
   and processing geography, quota/capacity, content-filter settings, offer
   terms, and estimated costs. Do **not** blindly accept **Default settings**.
4. For a short approved workshop, a supported pay-as-you-go/standard offer
   may suit better than provisioned throughput. Provisioned capacity can
   incur commitment/standing costs. Obtain customer approval for the actual
   offer. Do not purchase provisioned capacity or change geography to bypass
   quota without approval.
5. Enter a customer-chosen deployment name, for example `workshop-chat`.
   If the UI generates a name, privately record the **actual deployment
   name**, not merely the catalog model family.
6. Submit the approved deployment. Wait for **Succeeded / Ready** and
   inspect the deployment details for model/version/type/location.
7. In a new prompt-agent model selector confirm that this deployment is
   available. Actual runtime access is confirmed in section 8.
8. If no eligible model exists, stop. The customer requests quota or approves
   a supported alternative region/model and reassesses residency/cost.
   Never use an instructor model, an external API key, or a preview
   instant-model shortcut to mask the blocker.

**Checkpoint:** Your own named deployment is ready with an approved
compatibility, quota, and cost decision. Record it privately.

## 7. Review Monitoring and the Browser File Path

1. Current Foundry quickstarts include **Application Insights connection**
   setup before running agents. Review the [official tracing guide](REFERENCES.md#official-product-guidance)
   and your customer policy rather than assuming monitoring is free,
   universally optional, or already configured.
2. Where your portal flow requires a connection, open **Agents > Traces >
   Connect**. If Connect is absent, use **Manage > Project details >
   Connected resources > Add connection > Application Insights**.
   Select an approved **customer-owned** resource and choose **Connect**,
   or choose **Create new** and complete the browser wizard. Wait for the
   connection confirmation. If creating a resource, review
   subscription, dedicated RG, region, Log Analytics workspace, pricing,
   retention, access and network requirements before customer approval.
   Follow the official browser connection steps for the current labels.
3. Keep the approved project-managed-identity/Entra-only ingestion setting
   when required. Never paste monitoring keys into this repository.
   Trace-reading and ingestion permissions differ; customer admin verifies
   both. Do not broaden trace access to all attendees by default.
4. Enable only customer-approved tracing and diagnostic content. Prompts,
   retrieved passages and replies can be sensitive even in a learning
   environment. This workshop uses only synthetic documents. Manual scoring
   does not require paid automated evaluators.
5. If your approved configuration does not require traces for the lab,
   record that decision. If required tracing cannot be configured, mark
   readiness `BLOCKED`; do not claim a trace from a successful chat alone.
6. In this repository open each core file linked below. Use GitHub's
   **Download raw file** button; alternatively open **Raw** and use the
   browser's **Save as** to save the text, not the HTML page. Verify the
   name and `.txt` extension. Or use **Code > Download ZIP**, then select
   only the four text files when uploading, if permitted by customer policy.
7. Open/preview the downloaded plain text with your approved browser/file
   picker. It should begin with the corresponding `CONTOSO ORDEROPS`
   heading, not HTML or a sign-in page. Do not upload the ZIP or the whole repo.

| Required upload | Expected document identity |
|---|---|
| [order-policy-portal-2026-11.txt](../assets/order-policy-portal-2026-11.txt) | OPS-PORTAL-2026-11, CURRENT |
| [order-policy-archive-2025.txt](../assets/order-policy-archive-2025.txt) | OPS-ARCHIVE-2025-01, WITHDRAWN |
| [inventory-snapshot-2026-11.txt](../assets/inventory-snapshot-2026-11.txt) | INV-DEMO-2026-11-04, STATIC |
| [delivery-notes-2026-11.txt](../assets/delivery-notes-2026-11.txt) | DELIVERY-DEMO-2026-11 |

**Checkpoint:** Bootstrap is complete, approved monitoring is addressed,
and the participant can download/upload the four English plain-text files.
Do not upload instructions, answers, or the optional attack file as core data.

## 8. Create the Baseline Agent

This is also [Lab 1](LABS.md#lab-1-create-your-baseline).

1. Verify the project and customer identity. Open **Build > Agents >
   Create agent** and choose **Prompt / Text agent** if a type is offered.
   Do not select Hosted Agent, Workflow, Voice, or a code harness.
2. Name it `orderops-baseline`, or your own unused equivalent.
3. Select the **actual deployment** from section 6. If the selector proposes
   a new deployment, cancel that proposal and ask the customer model
   operator to resolve visibility/eligibility.
4. Inspect **Tools / Toolbox / Knowledge**. No tools should be attached:
   no File Search, Web Search, connectors, Code Interpreter, MCP, or custom
   functions. Detach accidental defaults from **your agent only**; do not
   delete shared customer toolboxes or connections.
5. Open [starter instructions](../prompts/01-starter.txt) in this repo.
   Copy the text into **Instructions**, not the chat box. Replace the three
   TODO lines with your own rules without copying inventory figures or
   answers into the prompt.
6. Select **Save / Create version**, or wait for confirmed autosave.
   Record the actual agent/version and instructions revision privately.
7. Open the agent's test chat/Playground. Start a fresh conversation and
   ask E01 from [the exact questions](../prompts/03-test-questions.txt).
   Wait for the reply; repeat E03 and E05 each in a fresh conversation.
   Record the three baseline results before adding knowledge.
8. If approved tracing is enabled, verify a corresponding new trace using
   the official monitoring instructions and your own access. Do not claim
   trace capture if you cannot see it.

**Checkpoint:** The customer's own baseline exists, uses their deployment,
has no tools, and has three honest observations. Missing-source answers
are expected; invented citations are failures, not successful grounding.

## 9. Create Your Grounded Agent and Knowledge Store

This is also [Lab 2](LABS.md#lab-2-create-and-attach-your-knowledge).

1. Create a **second** prompt agent named `orderops-grounded`, with the same
   model and the baseline instructions you actually tested. A duplicate
   action is optional; verify a duplicate did not inherit unexpected tools
   or conversation attachments. Keep the baseline ungrounded and unchanged.
2. In the grounded agent open **Tools / Toolbox / Knowledge > Add** and
   select **File Search**. Some rollouts expose the vector-store creation
   action under project files/knowledge first, then select that store from
   the agent. Use **File Search**, not Foundry IQ, a Search knowledge base,
   Web Search, or a classic "On Your Data" flow.
3. Choose **Create vector store / Add files / New knowledge** as available
   for that File Search function in **this project**. Use
   `orderops-knowledge-en` when naming is offered. If a name is generated,
   record the actual store identity privately.
4. Upload exactly the four core `.txt` files from section 7. Do not add
   `untrusted-note.txt`, prompts, evaluation notes, or real customer data.
5. Open the store/file list and wait until **all four** files report
   **Completed / Ready**. Inspect failures per file. "Uploaded", a spinning
   indexer, or merely seeing four filenames is not completion.
6. Review actual store expiry/retention and billing information if shown.
   If not exposed, ask the customer's service owner to establish it using
   approved service information. There is **no promised seven-day expiry**.
7. Select that newly created store for File Search on **orderops-grounded**
   and confirm the attachment. Verify the same project and all four core
   file identities. Store creation alone does not attach it to an agent.
8. Save/create a version and record the saved configuration. Reopen it and
   confirm **only File Search** and the intended store are attached.
   Check the baseline still has **no tools**.

**Checkpoint:** The grounded agent's saved version uses the customer's own
store, all four files are Completed, the attack document is absent, and the
baseline remains unchanged. If create/upload/index/attach is not exposed
in your rollout, capture a non-sensitive blocker and consult your customer
admin plus [troubleshooting](TROUBLESHOOTING.md). **Readiness is `BLOCKED`.**
Do not use a prepared external agent or paste context and call it retrieval.

## 10. Verify Actual Retrieval and Record Customer Evidence

1. Start a **fresh** chat with the saved grounded version. Ask E01 from the
   exact question file. Expand a real citation/source marker, open its
   original text, and confirm the current policy ID, CURRENT status, and
   quantity rule. A generated "Source: filename" line is not enough.
2. In a second fresh chat ask:

   ```text
   How many CD-100 are available according to the inventory snapshot?
   State the snapshot date and source. Is this a live query?
   ```

3. Open the returned inventory source. Confirm **12 units**, **2026-11-04,
   08:00, Europe/Berlin**, and **static, not live ERP**. Verify the
   original passage, not only the model's paraphrase.
4. If a claim needs multiple sources, inspect each essential source.
   Available approved tool/trace evidence may support diagnosis, but
   model-generated citation syntax is never technical evidence.
5. If the source panel cannot open a relevant source passage, or actual
   retrieval evidence cannot be established, the retrieval checkpoint is
   `BLOCKED`. Record why; do not declare cloud acceptance on a correct
   answer alone.
6. Use the [private results template](EVALUATION.md#private-results-template).
   Record timestamp, customer project label, model/version, agent/version,
   store/file completion, actual opened passage, result, and blocker.
   Do not publish customer identifiers, portal deep links, traces, or data.
7. Continue [Lab 3](LABS.md#lab-3-improve-instructions-and-compare) for the
   reference schema and complete [customer acceptance](FACILITATION.md#customer-acceptance-checklist).

**Checkpoint:** Your own customer-run source readback has occurred and is
documented. This repository's published evidence remains
**ACTUAL CUSTOMER END-TO-END: `NOT_RUN`** until a customer performs and
records their own complete acceptance. Merely following setup instructions
on paper or downloading this repo does not change that status.

## Optional: Reuse Only an Approved Customer Environment

The default above starts from zero. A customer may instead approve use of
an existing **customer-owned** resource/model after verifying isolation,
permissions, region, model compatibility, capacity, retention and cost.
Still create new workshop agents and a new four-file store, record actual
ownership, and restrict cleanup to those identified artifacts. Never treat
an instructor environment, historical seed index, or shared external
credential as an approved starting point.
