# Cloud Days: Customer-Owned Foundry Agent Workshop

**English | Browser only | From zero | Materials reviewed: 2026-11-09 | Access onboarding updated: 2026-11-10**

Build a fictional Contoso OrderOps prompt agent in **your own Microsoft
Foundry environment**. Create your resource group, Foundry resource, project,
model deployment, agents, and document knowledge yourself, subject to your
organization's approvals. No existing workshop cloud resources are needed.

## Customer-Owned Isolation Contract

- Every operational resource belongs to the customer's approved Azure
  subscription and directory. Customer identities create and administer it.
- Customers receive **no access to instructor resources**: no instructor
  subscription, tenant, project, model, agent, storage, index, endpoint, or
  credentials. Do not create guest identities in an instructor directory.
- The instructor supplies these public synthetic materials and facilitates
  learning. The instructor does not supply hosted infrastructure or accounts.
- Your customer administrator approves permissions, billing, region, network,
  monitoring, retention, and deletion. Participants build and test using their
  own customer-managed identities. Never share passwords or MFA codes.
- Basic setup uses service-managed backing storage for your customer project;
  that is not instructor storage. If policy requires storage in your own
  Azure resources, the customer must approve and configure Standard setup.
  See [the setup decision](docs/CUSTOMER-SETUP.md#3-choose-the-agent-environment).

## Start Here

| What you need | Read |
|---|---|
| Complete from-zero creation, with checkpoints | [Customer setup](docs/CUSTOMER-SETUP.md) |
| Customer administrator permissions and bootstrap | [Admin guide](docs/ADMIN.md) |
| Create, ground, improve, and challenge agents | [Browser labs](docs/LABS.md) |
| 210-minute learning session, separate setup time | [Agenda](docs/AGENDA.md) |
| Ten questions, expected answers, scoring | [Evaluation](docs/EVALUATION.md) |
| Customer admin and instructor delivery checklist | [Facilitation](docs/FACILITATION.md) |
| Billing, retention, and authorized deletion | [Costs and cleanup](docs/COSTS-CLEANUP.md) |
| Empty project, permissions, model, or search blockers | [Troubleshooting](docs/TROUBLESHOOTING.md) |
| Official documentation and UI limitations | [References](docs/REFERENCES.md) |

**Workshop-day access support:** We will help participants configure their
Foundry access in **their own Azure subscriptions, using their own Microsoft
Entra identities**, as far as their permissions and customer prerequisites
allow. Start with [assisted access in Lab 0](docs/LABS.md#lab-0-configure-and-verify-your-customer-access).
Bring your customer sign-in and MFA, an approved active customer subscription,
and a reachable customer administrator for any required access approvals or
role assignments. Facilitators guide the browser steps; they do not supply
accounts, subscriptions, administrator rights, or hosted Foundry resources.

**Default path:** prepare approvals and complete setup sections 1-7 before
the session where possible. If access is not ready, use the workshop-day
support in Lab 0 to work through the missing steps with your customer admin.
Complete the required setup before Lab 1. Setup sections 8-10 remain the
creation and retrieval instructions used during Labs 1-2; no prepared cloud
agent or preindexed knowledge base is a prerequisite.

Allow **60-90 minutes or more for technical setup**, preferably as prework or
in a separate setup clinic on the workshop day, plus your organization's
approval/identity/quota/network lead time. Lab 0 includes time-boxed access
support, not a guarantee of resolving every blocker. The **210-minute learning
agenda** does not include full first-time administrator approval and
infrastructure bootstrap.

## What You Need

A current approved browser, internet or approved private-network connectivity,
your corporate Microsoft Entra sign-in and MFA, an active **customer** Azure
subscription, an approved spending owner, a supported model/region with quota,
and permissions described in the [admin guide](docs/ADMIN.md). Customer admin
consent and organizational restrictions cannot be bypassed.

**Foundry User alone cannot create a Foundry account, deploy models, or assign
roles.** An authorized customer administrator performs those steps if you
cannot. Azure Owner/Contributor alone does not grant Foundry data actions.

No SDK, CLI, Python, Git, VS Code, Codespaces, Cloud Shell, local service,
API key, or `.env` file is needed to take this workshop. GitHub is a document
viewer, not a required development environment. Use the repository's file view
and **Download raw file**, or **Code > Download ZIP** in the browser, when
customer policy permits. Only the four core text files are uploaded to Foundry.
If download/upload or required portal actions are unavailable, record
`BLOCKED`; do not move to shared instructor resources.

## What Gets Created and Who Pays

| Component | Owner and purpose |
|---|---|
| Dedicated resource group and Foundry resource | Customer; infrastructure and billing boundary |
| Project and its managed identity | Customer; agent/data access boundary |
| Model deployment | Customer; billed usage or committed capacity according to selected offer |
| Two prompt agents and saved versions | Customer; baseline without tools and grounded agent |
| File Search store and four uploaded files | Customer project; indexing/storage and search charges may apply |
| Conversation history; approved monitoring | Customer responsibility; retention and additional costs apply |
| Optional Standard backing resources | Customer Storage, Search, Cosmos DB and networking, if required |

**Browser-only does not mean free.** There is no live ERP, reservation,
order submission, saved order draft, custom function, or technical approval
transaction. The inventory is a static synthetic document. A chat confirmation
does not execute anything. Every response must remain **RECOMMENDATION ONLY**.
Prompts and manual testing are not deterministic backend validation.

## Self-Contained Learning Materials

| File | Purpose |
|---|---|
| [Current policy](assets/order-policy-portal-2026-11.txt) | Current rules, including maximum quantity 20 |
| [Withdrawn archive](assets/order-policy-archive-2025.txt) | Deliberate conflicting source |
| [Inventory snapshot](assets/inventory-snapshot-2026-11.txt) | Four fictional products, fixed timestamp |
| [Delivery notes](assets/delivery-notes-2026-11.txt) | No documented delivery commitments |
| [Untrusted note](assets/untrusted-note.txt) | Optional controlled attack; **not in the core store** |
| [Starter instructions](prompts/01-starter.txt) | Write your first rules without embedding inventory |
| [Reference instructions](prompts/02-reference.txt) | Compare a fuller response schema and boundaries |
| [Exact ten test questions](prompts/03-test-questions.txt) | Reproducible manual experiments |

All required assets and prompts are in this repository. No operational
download points to another workshop repository. Names such as
`rg-orderops-workshop`, `orderops-workshop`, `workshop-chat`,
`orderops-baseline`, `orderops-grounded`, and `orderops-knowledge-en` are
**examples, not existing resources**. Choose your own unused names.

## Evidence and Readiness

**ACTUAL CUSTOMER END-TO-END: `NOT_RUN`.** These are locally checked materials,
not proof that any customer tenant, permissions, rollout, model, or File Search
path has passed. No customer deployment is included or performed by this
repository. There are no provisioning scripts, deployment workflows, secrets,
private mappings, or instructor screenshots.

The customer must perform the [acceptance checklist](docs/FACILITATION.md#customer-acceptance-checklist)
and record real source passages and results privately. An unavailable portal
upload/index/attach/source path is `BLOCKED`, not a passed retrieval exercise.

## License and Origin

[MIT license](LICENSE). Original synthetic OrderOps assets and prompts are
reused with their copyright notice. This is a separate customer-owned
browser learning path, not an infrastructure export or a copy of another
repository's Git history. Official Learn links provide product guidance;
they do not grant Azure access or override customer policies.
