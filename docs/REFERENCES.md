# Official References and Validation Boundary

[Home](../README.md) | [Customer setup](CUSTOMER-SETUP.md)

**Reviewed: 2026-11-09.** Product documentation and portal rollouts can change.
Links are generic public product guidance, not workshop resources, accounts,
credentials or endpoints. Read the **Foundry portal** tab when an article
also offers SDK/CLI examples. Those other tracks are not prerequisites here.

## Official Product Guidance

| Topic | Official source | Use in this workshop |
|---|---|---|
| New resource/project and model creation | [Set up Foundry resources](https://learn.microsoft.com/en-us/azure/foundry/tutorials/quickstart-create-foundry-resources) | Project picker, Advanced options, deployment review; model names are examples |
| Control/data roles and project identity | [Foundry RBAC](https://learn.microsoft.com/en-us/azure/foundry/concepts/rbac-foundry) | Project-scoped participant role, parent Reader, separate model/runtime access |
| Prompt agents in the portal | [Prompt agent quickstart](https://learn.microsoft.com/en-us/azure/foundry/agents/quickstarts/prompt-agent) | No portal installation; model, instructions and tools |
| No-code portal vs. code tracks | [Get started](https://learn.microsoft.com/en-us/azure/foundry/quickstarts/get-started-code) | Select portal tab; no local tooling for this workshop |
| Basic, Standard and private setup | [Agent environment setup](https://learn.microsoft.com/en-us/azure/foundry/agents/environment-setup) | Customer architecture/admin chooses actual backing-resource design |
| Customer-provisioned backing resources | [Use your own resources](https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/use-your-own-resources) | Standard requirements; some documented methods are code/template-based and not a universal browser path |
| Network-isolated setup | [Private networking](https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/virtual-networks) | Customer network prerequisites; do not bypass restrictions |
| File Search | [File Search tool](https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/tools/file-search) | Own files/store, wait for ingestion, attach, verify source, additional charges |
| Model/service quotas and support | [Agent limits, quotas and regions](https://learn.microsoft.com/en-us/azure/foundry/agents/concepts/limits-quotas-regions) | Check current eligible model/version/region/setup, not a hardcoded promise |
| Foundry region availability | [Region support](https://learn.microsoft.com/en-us/azure/foundry/reference/region-support) | Verify all required features in customer-approved geography |
| Monitoring connection, trace privacy/access | [Set up agent tracing](https://learn.microsoft.com/en-us/azure/foundry/observability/how-to/trace-agent-setup) | Customer Application Insights connection, separate reader rights, actual trace verification |
| Assign roles in the browser | [Azure portal role assignments](https://learn.microsoft.com/en-us/azure/role-based-access-control/role-assignments-portal) | Customer administrator only, correct role and scope |
| Provider registration | [Resource providers and types](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/resource-providers-and-types) | Subscription administrator registers only required providers |
| Budgets and alerts | [Create and manage budgets](https://learn.microsoft.com/en-us/azure/cost-management-billing/costs/tutorial-acm-create-budgets) | Alerts are not a hard spending cap |
| Agent Service billing | [Foundry Agent Service pricing](https://azure.microsoft.com/en-us/pricing/details/foundry-agent-service/) | Model/tool/storage and setup-specific costs must be reviewed |
| Azure OpenAI and File Search pricing | [Azure OpenAI pricing](https://azure.microsoft.com/en-us/pricing/details/cognitive-services/openai-service/) | Check actual model/deployment offer and search charges |

## Portal UI and Validation Boundary

- The new-resource Learn guide (updated 2026-10-27) documents the first-use
  project picker and existing-project picker, Advanced options and base-model
  deployment. Review customer defaults rather than accepting them blindly.
- The RBAC guide (updated 2026-10-30) distinguishes resource creation,
  model management, data actions and conditional role-assignment powers.
  Older Azure AI role labels may remain during the rename.
- The File Search guide (updated 2026-10-23) is heavily SDK-oriented but
  also references portal upload/vector-store creation. That is not proof
  of an identical upload/attach dialog in every customer's current rollout.
- Agent and toolbox labels can differ. This repository describes required
  functions and observable checkpoints; it does not invent a guaranteed
  click label, citation viewer, or enterprise no-code provisioning wizard.
- Current prompt-agent quickstarts and tracing guidance include Application
  Insights setup. Apply customer approval, privacy, retention and separate
  trace-reader requirements. A successful response is not a verified trace.
- No instructor-environment screenshots are reused or rebranded. Official
  Learn pages contain product illustrations for context. Customer screenshots,
  if created privately, require their normal data-sharing review.

**Local validation is not customer cloud acceptance.** The materials' file
links, heading anchors, synthetic invariants, prompt reuse, question/rubric
alignment and agenda can be checked locally. Model availability, portal
capabilities, authorization, network, ingestion, retrieval and actual replies
must be tested in the customer's own approved environment.

**ACTUAL CUSTOMER END-TO-END: `NOT_RUN`.** Missing required portal functionality
means **BLOCKED**. Do not fall back to shared instructor resources, paste
context and claim retrieval, or label an unexecuted path as passed.
