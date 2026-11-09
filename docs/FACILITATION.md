# Customer Admin and Instructor Facilitation

[Home](../README.md) | [Admin](ADMIN.md) | [Setup](CUSTOMER-SETUP.md) | [Agenda](AGENDA.md)

## Responsibilities

| Person | Owns |
|---|---|
| Customer subscription/security owner | Subscription, approvals/consent, billing, residency, network, retention |
| Customer resource/model administrator | From-zero bootstrap, model quota/deployment, targeted IAM and managed-identity verification |
| Customer participant | Their corporate sign-in, agent/store creation, source inspection and private results |
| Instructor/facilitator | Public materials, learning discussion, manual rubric and non-sensitive troubleshooting |
| Customer cleanup owner | Approved artifact inventory, deletion decision, verification and final cost review |

An instructor identity has no required Azure role. Do not collect customer
participant emails to provision workshop accounts. The customer's internal
directory team manages its own users/groups. No bulk account creation,
initial-password export, shared credentials, guest invitation into an
instructor tenant, or instructor-hosted store is part of this workshop.

## Before the Learning Session

1. Send this repository's [home page](../README.md), [setup](CUSTOMER-SETUP.md),
   [admin guide](ADMIN.md), and [costs](COSTS-CLEANUP.md) to the customer
   through their approved channel. The customer owns approvals.
2. Plan **60-90 minutes or more** technical prework after organizational
   approvals; reserve separate lead time for identity, quota and network.
   Do not promise this bootstrap fits inside 210 teaching minutes.
3. Default to **one participant per project** in the customer environment.
   Team projects are allowed only as an explicit customer-approved common
   access boundary. Team members use separate identities and coordinate
   agent names/versions; agents alone do not isolate their shared files.
4. The customer admin follows setup 1-7 and verifies the restricted
   participant path. Participants create their agents and stores in Labs 1-2.
   If a customer rehearses the full path, use a separately labeled customer
   test project or preserve the real rehearsal evidence. No instructor
   resource is needed for either rehearsal or delivery.
5. Estimate concurrency from actual model TPM/RPM quota and planned prompts,
   not attendee count alone. Start in small customer-managed waves, such as
   a few learners at a time; watch actual latency and 429s, then adjust.
   Never assume a fixed wave size guarantees capacity.
6. Agree on cost budget alerts and recipient/action owner. Budget alerts
   **do not stop Azure spending**. Disable optional paid automated evaluators
   for the required manual-scoring path where the UI offers them.
7. Confirm File Search upload/index/attach/source-readback capabilities in
   the customer's actual new-portal rollout. No screenshots or service
   examples establish this on their behalf.
8. Agree on privacy for screen sharing, recorded sessions, notes and traces.
   Use synthetic content only. Keep customer IDs, endpoints and raw
   telemetry out of public issues, slides and this repository.

## Customer Acceptance Checklist

**Initial status for every row: `NOT_RUN`.** The customer records actual
time, reviewer, evidence and `PASS / FAIL / BLOCKED / NOT_RUN` privately.
The repository does not assert a completed customer cloud run.

| Check | Evidence needed |
|---|---|
| Customer ownership | Correct corporate identity, directory, active subscription and dedicated workshop scope verified |
| Approvals | Cost owner, region/geography, quota, network, model terms, trace/retention and cleanup decision recorded |
| Resource bootstrap | New RG, Foundry resource and project ready; deployment state Succeeded |
| Control/data separation | Participant project Foundry User, parent Reader when required; no unnecessary broad admin assignment |
| Runtime identity | Correct project managed identity and model/backing-resource roles verified |
| Individual access | Each participant signs in with their own customer identity; no shared passwords |
| Model | Actual customer deployment ready and works from participant's prompt agent; version/type recorded |
| Baseline | Participant-created no-tool agent; E01/E03/E05 observations recorded before grounding |
| Grounded artifact | Participant-created second agent, correct saved version and same customer model |
| Four-file store | Participant-created store, all four English texts Completed, no attack note |
| Attachment | Only File Search with that same-project store on grounded agent; baseline unchanged |
| Actual sources | E01 current-policy passage and snapshot passage opened; English text, fixed timestamp, no live query |
| Core behavior | E01/E03/E05/E06/E07/E09 all run; at least 30/36 and no hard failures |
| Ten-test completion | E02/E04/E08/E10 also run/scored; no hard failures; E10 labeled quoted-context |
| Isolation | Customer checks memberships/inheritance and confirms no unauthorized cross-project data/build access |
| Monitoring | Approved connection/settings/reader scope verified as required; actual trace verified if claimed |
| Lifecycle | Actual expiry/retention question resolved or explicitly escalated; artifacts, deletion owner/date and costs recorded |

If any required creation, attachment, citation, permission or support action
is missing, readiness is **BLOCKED**. An administrator's successful chat
does not pass the restricted participant check. Watching a team demo does
not pass an individual's own cloud test.

## During the 210 Minutes

1. Explain the boundary first: recommendations only, no ERP or transaction.
   For the opening demonstration use the synthetic documents as a browser
   reading exercise, or a willing customer's already-approved test run
   inside their own environment. Instructor cloud access is never required.
2. At Lab 0 check readiness, not new subscriptions. Escalate bootstrap
   problems to the customer's own administrator.
3. Run question waves with one outstanding request per learner; pause on
   throttling. Use shorter replies, wait for the service's retry guidance,
   and reduce parallel demand before considering any approved capacity change.
4. At Lab 2 require all four Completed and real opened passages. A pasted
   answer, matching filename or generated citation is not retrieval proof.
5. Use fresh conversations and record versions. Encourage honest failures;
   never convert `NOT_RUN` into a guessed pass.
6. Keep the optional retrieval-attack challenge separate from the core store.
   It needs customer owner authorization and extra retention/cost review.
7. Collect only anonymized synthetic learning observations if the customer
   allows it, not portal inventories or credentials.

## Recover Without Shared Infrastructure

- **Access/RBAC:** Customer administrator diagnoses the denied action,
  confirms scope and identity, grants only approved targeted access and
  retests after propagation. No attendee blanket Owner workaround.
- **Quota/429:** Pause or use fewer concurrent requests. The customer's
  capacity owner can request quota or approve changes. Never borrow an
  instructor deployment.
- **Upload/policy:** Customer IT approves a browser transfer route on customer
  equipment. No covert file transport, local script, or external seed index.
- **UI/File Search missing:** Verify new portal, prompt-agent type,
  model/region/setup and permissions. If the required browser feature is
  unavailable, record `BLOCKED` and continue only with an explicitly
  non-executed document/rubric discussion.
- **Individual blocked:** With customer consent, the person may observe
  a team member's customer-owned demo. No password sharing. Their individual
  acceptance stays blocked and needs a later own-account rerun.
- **Service unavailable:** Use the synthetic sources for paper analysis,
  schedule a continuation, and record no cloud pass.

These are teaching recovery paths, not permission to change customer
policy or to present a different architecture as the requested workshop.

## After the Session

The customer stores actual test results privately, reviews costs and
retention, approves the exact deletion set, and follows
[cleanup](COSTS-CLEANUP.md#authorized-cleanup-in-the-browser).
Remove only workshop-specific approved access grants after dependencies
are checked. Keep ordinary corporate identities and production permissions
untouched. No instructor account lifecycle is involved.
