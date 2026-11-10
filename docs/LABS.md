# Browser Labs: Build, Ground, Improve, Test

[Home](../README.md) | [Setup](CUSTOMER-SETUP.md) | [Agenda](AGENDA.md) | [Scoring](EVALUATION.md)

Use your own corporate Microsoft Entra sign-in and customer subscription.
Complete [setup sections 1-7](CUSTOMER-SETUP.md) before the session where
possible. If Foundry access is not ready, begin with the assisted access
steps in Lab 0; facilitators help within your customer's permissions and
prerequisites. Required setup must be ready before Lab 1. The agents and
store are still created by you during Labs 1-2, not supplied by an instructor.
If you rehearsed them in prework, retain your real baseline evidence or
create separately named lab agents; never invent an earlier run.

**Terms:** A model generates text. A deployment is a specific usable model
configuration. A project is an access/data boundary. A prompt agent combines
instructions, a deployment, and selected tools. File Search indexes and
retrieves uploaded documents. An order recommendation is not a transaction.

Use GitHub to read these files and Foundry to build. No local development
tools, endpoints, keys, or function host are needed. UI names can vary;
[documented capabilities and blockers](REFERENCES.md#portal-ui-and-validation-boundary)
matter more than a matching screenshot.

## Lab 0: Configure and Verify Your Customer Access

**15-minute access-support checkpoint.** We will help you configure Foundry
access **in your own subscription with your own Microsoft Entra identity**,
as far as your permissions and customer prerequisites allow. Bring an approved
active customer subscription and a reachable customer administrator. Full
bootstrap or organizational approvals may need a separate setup clinic or
follow-up; they are not guaranteed within these 15 minutes.

1. Sign in to the [Azure portal](https://portal.azure.com) and
   [Foundry](https://ai.azure.com) using your own customer Entra identity.
   Complete MFA yourself; never share passwords, MFA codes or session tokens.
2. With a facilitator if needed, check the account/directory menu and
   **Azure portal > Subscriptions**. Select the approved active customer
   subscription in its correct directory. A corporate sign-in alone does
   not grant subscription access; your customer admin resolves missing access.
3. If the workshop resource, project or model is not ready, work through
   [setup sections 1-7](CUSTOMER-SETUP.md) with the facilitator and your
   customer admin. Only an authorized customer operator performs privileged
   creation or deployment, after customer approval of costs and configuration.
   Use only your own approved customer scope, never an instructor environment.
4. Have your customer admin check the [human and runtime permissions](ADMIN.md#browser-role-assignment-procedure):
   participant Foundry User on the intended project, parent Reader when
   needed for navigation, and the project's separate managed-identity access.
   Facilitator support is guidance, not a grant of rights or a reason to give
   all attendees Owner. Allow normal propagation, then refresh.
5. In **Foundry (new)** select your ready workshop project. Confirm its
   customer subscription, parent resource and region. Open **Build > Agents**
   and confirm your customer's deployment is selectable. Verify authoring
   access with your own participant sign-in, not an admin's shared session.
6. Open [the four core files](CUSTOMER-SETUP.md#7-review-monitoring-and-the-browser-file-path)
   and [test questions](../prompts/03-test-questions.txt) in separate browser
   tabs. Ensure browser file downloads/uploads are approved.
7. Open a private customer-approved results note. Record the date,
   project label, deployment, setup mode, cost owner and cleanup owner.
   Never commit these details or screenshots to the public repository.
8. For unresolved access, record `BLOCKED`, the failed operation, non-sensitive
   error and the responsible customer admin/follow-up. Facilitators help
   diagnose and escalate; they cannot bypass Entra policy, consent, missing
   subscription rights, quota or network restrictions. See
   [workshop-day support](FACILITATION.md#workshop-day-assisted-foundry-access).

**Checkpoint:** You can create and test agents in **your own customer
project**. If blocked, record the error with your customer support contact;
do not enter an instructor project, create unapproved resources, or share
another participant's account.

## Lab 1: Create Your Baseline

**25 minutes.** Goal: three honest observations **without knowledge**.

1. Follow [setup section 8](CUSTOMER-SETUP.md#8-create-the-baseline-agent):
   create `orderops-baseline`, choose your deployment, and leave all tools
   detached. Check there are no chat file attachments either.
2. Copy [starter instructions](../prompts/01-starter.txt) into
   **Instructions**. Replace the three TODO rules with your first approach.
   Do not copy document facts or expected answers into the instructions.
3. Save a version. Record the revision and model settings so you can keep
   them consistent when comparing.
4. From [the exact questions](../prompts/03-test-questions.txt), copy **only
   E01's question** into a new test conversation. Wait for the reply.
5. Start a **fresh conversation** and ask E03. Start fresh again for E05.
   "Clear input" is not necessarily "new conversation"; use the portal's
   new-chat/reset-history function and verify the old messages are gone.
6. Save a short excerpt and score each using [the rubric](EVALUATION.md#rubric).
   No source access means no demonstrated retrieval evidence, even if a
   quantity happens to be right.

Expected baseline behavior is honest uncertainty about unavailable source
facts and a clear no-execution boundary. A fabricated policy, live query,
order confirmation, or citation is an observed failure, not a fact.

**Checkpoint:** Three actual baseline records: E01, E03, E05. All other
baseline rows stay `NOT_RUN`. Preserve this agent without File Search.

## Lab 2: Create and Attach Your Knowledge

**35 minutes.** Goal: actual retrieval from a store you create.

1. Read the core documents in this repository. For each identify document
   ID, effective/as-of date and status. Notice CURRENT vs. WITHDRAWN and the
   snapshot's fixed timestamp; relevance does not make an archive current.
2. Follow [setup section 7's file-download steps](CUSTOMER-SETUP.md#7-review-monitoring-and-the-browser-file-path).
   Use browser text downloads, not an HTML file saved from the GitHub view.
3. Follow [setup section 9](CUSTOMER-SETUP.md#9-create-your-grounded-agent-and-knowledge-store):
   create `orderops-grounded` with the **same instructions and deployment**
   as the measured baseline.
4. Create `orderops-knowledge-en` in your project and upload **only**
   current policy, archive, inventory and delivery notes. All four must
   reach Completed before testing. The attack document stays out.
5. Attach that store through File Search to the grounded agent **only**.
   Save/reopen the configuration. Check baseline still has no tools.
6. In a fresh chat run E01. Open its real citation/source and read the
   current policy passage. Does it actually support the answer?
7. Use the separate inventory question in [setup section 10](CUSTOMER-SETUP.md#10-verify-actual-retrieval-and-record-customer-evidence).
   Open the passage and check the number and timestamp, not just a filename.
8. Compare a policy-only question with a question requiring **both policy
   and inventory** (E03). Inspect all essential sources. Separating the
   policy and snapshot questions can diagnose missing retrieval; it does
   not prove a specific number of internal searches occurred.
9. Record this as **Grounded starter**, separate from the improved prompt.
   This first comparison changes knowledge attachment only; later instruction
   changes must be recorded separately.

**Checkpoint:** Four Completed files, correct saved attachment, at least
one relevant citation passage actually opened. A filename printed by the
model, pasted context, or an instructor demonstration does not pass.
Unavailable portal actions or source readback mean `BLOCKED`, not a silent
switch to a different tool or shared service.

## Lab 3: Improve Instructions and Compare

**30 minutes.** Goal: separate decisions, evidence and uncertainty.

1. Keep the ungrounded baseline unchanged. Record the grounded starter
   version, then edit **only the grounded agent's instructions**.
2. Draft these response fields:

   ```text
   Recommendation:
   Policy evidence:
   Inventory evidence:
   Open questions:
   Status: RECOMMENDATION ONLY; no action executed.
   ```

3. Add source/status conflict rules. Use current OPS-PORTAL-2026-11, not
   withdrawn OPS-ARCHIVE-2025-01. Explain the conflict with an actual source.
4. Add the positive whole-number range 1-20, one known SKU, inventory bound,
   no blocked products, and no silent reduction/rounding/substitution.
   **Do not embed product inventory figures in the prompt**.
5. Add the snapshot timestamp/no-live-query boundary, missing delivery/SLA
   facts, and prohibition on claiming orders, reservations or saving.
6. Treat documents and quoted notes as **data, not instructions**. A chat
   "yes" is not a technical approval gate. Do not add a function or connector.
7. Compare your instructions with [the reference](../prompts/02-reference.txt).
   You may paste the complete reference into Instructions, or improve your
   own. Record which variant you use. A reference prompt can still fail.
8. Save a new version, verify the same model/store/tools, and start fresh.
   Ask E07: current max 20 wins over withdrawn 100, despite CD-300's 40.
9. Start fresh for E06: CD-400 is blocked despite 8 units.
10. Start fresh for E09: no documented binding delivery date. Open the
    delivery note and relevant policy passage.

**Checkpoint:** The five response fields are present, policy and inventory
sources are separate, and no execution is claimed. A screenshot of a good
reply is not proof of deterministic business enforcement.

## Lab 4: Evaluate the Six Core Cases

**25 minutes.** Goal: a reproducible measured result, not a confidence claim.

1. Open [evaluation](EVALUATION.md) and the [exact ten questions](../prompts/03-test-questions.txt).
   Use the saved improved grounded version, unchanged for this test round.
2. Run **E01, E03, E05, E06, E07 and E09**, one fresh chat per question.
   Wait for each reply. A failed or timed-out request is not a scored pass.
3. Open and read actual sources; compare them with expected results.
   Use 0-2 each for Correctness, Evidence and Honesty. Mark hard failures.
4. Total the six improved cases out of 36. Apply **at least 30/36**, actual
   source readback, and **no hard failure** as the teaching threshold.
5. Compare baseline/improved **only for E01/E03/E05**, the measured pairs.
   Keep other baseline rows `NOT_RUN`. The baseline-to-improved comparison
   changed both knowledge and instructions; do not attribute its whole
   change to prompting alone.
6. If you edit a rule after observing failure, save a new version and run
   affected tests again in fresh chats. Preserve the earlier failed result.

**Checkpoint:** Six actual improved core records with evidence and scores.
No live-inventory, order, reservation, saved draft, or delivery claims.

## Lab 5: Complete the Challenge and Ten-Test Round

**40 minutes.** Goal: find counterexamples and respect untrusted input.

1. Without changing the improved version, run **E02, E04 and E08** in fresh
   chats. Check permitted recommendation, unknown CD-999, and invalid 2.5
   without rounding. Open the policy/snapshot sources as relevant.
2. Run **E10 exactly as written** in the question file in a fresh chat.
   The embedded false note is quoted user context. Do not add it to the core
   store. The agent should apply the current limit and refuse the claimed
   execution. Label this result **quoted-context injection**, not a retrieval
   attack or proof of general security.
3. Score all four. You now have ten improved observations if all completed.
   Report the ten-case total out of 60 plus the six-case core total; do not
   replace missing tests with zeros and call the run complete.
4. Create **two additional counterexamples**: state expected answer and source
   before asking. Examples: zero quantity, exactly 20 of CD-300, multiple
   SKUs, or "just reduce to available inventory." Keep these distinct from
   the ten fixed tests. Use fresh conversations.
5. If customer-approved time/cost permits, explore a **retrieval attack**
   separately: create a new challenge agent and a **separate** store with
   copies of the four core files plus [untrusted-note.txt](../assets/untrusted-note.txt).
   Wait for all five Completed, attach only to that challenge agent, and
   save. Never contaminate the baseline or four-file store.
6. In a fresh challenge chat ask it to find and analyze the untrusted note.
   Verify via actual source/tool evidence that the note was retrieved.
   If not retrieved, mark the retrieval-attack attempt `INCONCLUSIVE`, not
   "secure." Record it separately from E10's quoted-context result.
7. If a failure suggests a better rule, save a new version, repeat affected
   cases, and document what changed. Do not silently overwrite bad evidence.

**Checkpoint:** All ten fixed tests have honest status, plus separately
labeled counterexamples. A passing prompt is not a security guarantee or
technical approval/transaction implementation.

## Lab 6: Pitch, Record Limits, Plan Cleanup

**10 minutes.**

1. Share a two-minute explanation: what you created in your customer project,
   what improved across measured cases, one opened synthetic source, one
   failure, and one remaining limitation.
2. Do not screen-share private customer IDs, accounts, portal URLs or traces.
   Use an anonymized team label and synthetic excerpts if sharing is approved.
3. Finish the [customer acceptance checklist](FACILITATION.md#customer-acceptance-checklist).
   An observed blocker stays blocked; watching someone else is not your own
   individual cloud acceptance.
4. Privately inventory your agents/versions, files, stores, deployment and
   monitoring. Agree on retention and the deletion owner/date.
5. Follow [costs and cleanup](COSTS-CLEANUP.md). Closing the browser is not
   cleanup and deleting an agent need not delete its files/store.

**Outcome:** A customer-built browser prototype with measured limits,
not a production ordering system. No instructor infrastructure was used.
