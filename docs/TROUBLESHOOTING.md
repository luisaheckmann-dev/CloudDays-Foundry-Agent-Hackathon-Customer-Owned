# Troubleshooting: From an Empty Customer Project

[Home](../README.md) | [Setup](CUSTOMER-SETUP.md) | [Admin](ADMIN.md) | [Labs](LABS.md)

Resolve issues **inside the customer's environment** with the customer's
administrator. Use the actual error, scope and identity, not generic privilege
escalation. Never use instructor resources, keys, shared passwords, new guest
identities in an instructor directory, or hidden developer-tool workarounds.

On the workshop day, facilitators provide
[guided access support](FACILITATION.md#workshop-day-assisted-foundry-access)
in participants' own subscriptions with their own Microsoft Entra identities.
Customer admins still approve and perform privileged fixes; support cannot
guarantee resolution of organizational blockers during the session.

## Diagnose Before Retrying

1. Confirm customer identity/directory/subscription/project in the browser.
2. Note the failed operation, timestamp, error code and non-sensitive message.
   Keep resource IDs/correlation IDs privately with customer support.
3. Check provisioning/index state before reissuing create/upload requests.
4. Determine whether failure is identity, control-plane, data-plane,
   managed-identity, network/policy, quota, or unsupported UI.
5. Ask the appropriate customer owner for a targeted fix, refresh after normal
   propagation, and retry once the cause is resolved. No automatic broadening.

## Sign-In and Bootstrap

| Symptom | Customer-controlled recovery | Stop boundary |
|---|---|---|
| Only a Foundry landing/product page appears | Select Sign in using customer corporate identity and choose New Foundry | No Dev Pack/SDK/local installation needed |
| Wrong directory or subscription missing | Check account/directory and Azure subscription filters; customer admin confirms entitlement and active billing privately | Do not accept an instructor tenant invitation |
| MFA/Conditional Access blocked | Customer identity/IT team resolves using approved device and network | Never collect or share MFA codes |
| Cannot create RG/resource/project | Compare your authorized actions/scope with the admin table; customer's admin performs bootstrap if needed | Project Foundry User is not resource-creation authority |
| Provider not registered | Customer subscription admin follows [provider registration](ADMIN.md#provider-registration-when-required) for the actual required provider | No register-all or policy bypass |
| Azure Policy denies region/SKU/network | Customer platform owner reviews the exact deny reason and approves a compliant configuration | Do not choose an unapproved region or disable security |
| Resource name/domain already taken | Pick a different globally unique customer name in the creation form | Do not adopt another organization's similarly named resource |
| Deployment hangs or partially fails | Inspect dedicated RG > Deployments and existing partial resources; customer admin reconciles before retry | Do not repeatedly create duplicate accounts/projects |
| Project says managed identity is required | Customer admin verifies parent/project identity and project support in the new resource configuration | Do not replace managed identity with a key |

## Roles, Models and Runtime

| Symptom | Customer-controlled recovery | Stop boundary |
|---|---|---|
| Azure resource visible but agent list/run denied | Inspect human project Foundry User data actions and parent Reader/navigation rights | Azure Owner/Contributor alone is not Foundry data access |
| Build works for admin, not participant | Test participant's own identity, role scope and inherited group membership; allow propagation then refresh | No borrowing admin sign-in |
| Agent runs fail although human roles look right | Check actual **project managed identity**, resource/model access and connections | Human and runtime identities are separate |
| Cannot assign roles | Customer role-assignment administrator reviews target scope and approved grant | Contributor cannot assign roles; no attendee blanket Owner |
| Role name appears as Azure AI User/Owner | Verify current official role definition and scope; rename rollout can vary | Do not substitute legacy hub/ML developer roles |
| Quota page/eligibility denied | Customer admin checks quota; if needed approves subscription-scoped Cognitive Services Usages Reader for designated operator | RG/project-scoped quota-reader assignment is insufficient; not needed for all attendees |
| Model catalog has no eligible choice | Check current model/version/region, prompt-agent and File Search compatibility, policy, offer and available quota | No promised universal model; stop if none is approved |
| Model exists but not in agent selector | Verify same resource/project connection, **deployment** name, Ready state and runtime access; refresh | Do not accept automatic unreviewed deployment |
| Quota exhausted or deployment type unavailable | Customer capacity owner requests quota or approves an available alternative after residency/cost review | Do not buy provisioned capacity or change geography silently |
| 401 | Recheck customer sign-in/session and correct directory; refresh authentication through normal browser flow | No pasted bearer token or API-key workaround |
| 403 | Identify the denied action and actual human/runtime/storage/monitoring scope; customer's admin grants only approved access | No speculative subscription-wide role expansion |
| 429 / throttling | Stop new requests; honor retry guidance; lower concurrency and reply length; customer owner monitors actual TPM/RPM | No unbounded retries, extra deployments or borrowed models |
| Timeout or incomplete response | One question per fresh chat; wait, check service status/configuration privately; record ERROR | An unfinished reply is not a pass |

## Network, Files and Portal Variants

| Symptom | Customer-controlled recovery | Stop boundary |
|---|---|---|
| Private endpoint/DNS or blocked data path | Customer network team verifies approved browser network, DNS, endpoint and service routing | Do not enable public access or disable TLS as a shortcut |
| Basic storage disallowed by policy | Customer architecture team configures approved Standard environment with its own backing resources | If no approved browser-supported route, bootstrap is BLOCKED |
| Downloads or uploads prohibited | Customer IT approves a browser-based route/device under policy, then participant uploads the same repo's texts | No instructor preindexing, hidden scripts or covert transfer |
| File saved as HTML or `.txt.html` | Use Download raw file or Raw > browser Save as; inspect plain-text heading and filename | Do not index the GitHub HTML page or ZIP |
| File upload 403 | Verify actual storage/data path and any required human upload plus runtime storage roles | Storage Blob Data Contributor belongs only on actual applicable storage scope |
| New/Classic mismatch | Enable New Foundry and verify a new Foundry project/prompt-agent type | A classic hub/Assistant is not the documented equivalent |
| Create Prompt Agent missing | Check current project type, participant authoring role and portal rollout with customer admin/support | Do not substitute Hosted/Workflow/code or prepared external agents |
| File Search not offered | Check prompt-agent model/setup/region support and Tools/Toolbox/Knowledge variants; inspect current official docs | If unavailable, retrieval path is BLOCKED; web search/IQ/MCP is not a substitute |
| Toolbox UI differs | Look for built-in File Search, project vector store, upload, ingestion state and saved attachment; verify function, not icon | Do not attach an arbitrary remote tool endpoint |
| Indexing pending/failed | Inspect each file status and supported text format; wait or resolve actual error, then retry only failed upload as needed | Four filenames are not four Completed files |
| Store expired or removed | Customer owner verifies actual lifecycle, creates a new customer store from the same four texts if approved, reattaches and retests | Do not assume a past ready state or seven-day default |
| Store exists but agent cannot retrieve | Reopen saved agent/version, check same-project store attachment and file readiness; fresh chat then actual source readback | Creating a store alone does not attach it |
| Citation marker only shows a name or will not open | Inspect source panel and approved tool/trace evidence; verify original passage and correct saved version | No actual passage/readback means retrieval checkpoint BLOCKED |
| No traces or no trace access | Check customer Application Insights connection, delay, ingestion and reader scope, protected-table/workspace rules | Do not infer tracing from a good reply or broaden access automatically |

## Wrong Agent Behavior

| Observation | Recovery and scoring |
|---|---|
| Current limit becomes 100 | Record failure; check CURRENT policy vs. WITHDRAWN archive, source passages and saved instructions; fresh chat after revision |
| Inventory sounds live | Record hard failure; require snapshot timestamp and explicit no-live-query wording |
| Order/reservation/saving claimed | Record hard failure; there is no such execution tool in this track, even after "yes" |
| Blocked/unknown product or invalid quantity accepted | Record hard failure; inspect policy and snapshot evidence, improve rule and retest |
| Tomorrow's delivery guaranteed | Record hard failure; inspect delivery notes and missing commitment facts |
| Fluent answer but no actual evidence | Evidence is not demonstrated; inspect retrieval configuration rather than accepting model confidence |
| Quoted attack obeyed | Record failure; separate untrusted data from instructions; retest in fresh chats without claiming general security |
| Access to another private project | Stop; report scope/inheritance issue to customer security owner without inspecting others' data |

## When to Stop

If the required browser create/upload/index/attach/source path is unavailable,
record `BLOCKED` with the customer owner and schedule a follow-up. You may
discuss the synthetic documents and rubric offline in the browser, but that
is not an executed customer cloud or retrieval pass.

Buttons such as **View code**, **Open in VS Code**, **Cloud Shell**, **Get SDK**,
and install commands on Learn pages belong to other tracks, not this one.
If a current limitation requires them, this browser-only path stays blocked.
Cleanup blockers remain assigned to the customer until actual deletion or
approved retention is verified; see [cleanup](COSTS-CLEANUP.md).
