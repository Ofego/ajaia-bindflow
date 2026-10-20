# Ajaia Design Lead Assessment: Marsh & Colby

**Video:** [PASTE VIDEO LINK, with "Ajaia" in the title]
**Final designs (Figma):** https://www.figma.com/design/6xILGqurhKPLRyw19t8xMH/Gostride?node-id=31-2  
**Clickable prototype (responsive):** https://ofego.github.io/ajaia-bindflow/prototype/  
**Repo:** https://github.com/Ofego/ajaia-bindflow
**Candidate:** Arerosuoghene Omujale · Portfolio: https://ofego.design
**Prepared for:** [Ajaia](https://ajaia.ai)

---

## Task 1. Synthesis and next questions

### The core finding

Owen's wishlist speeds up the **checklist**. The evidence says the checklist is the **fastest** part of the job. Colin completes it in an average of 3 minutes once he has the documents (M4), and both assistants describe it as something they know by heart (M1, M2).

The time goes to two other places:

1. **Gathering the documents:** 11 minutes per submission for Colin.
2. **Resolving mismatches with brokers:** a median of 2.1 days for Anika.

Even Owen agrees the checklist itself is fine: *"Our assistants know the checklist inside and out so I don't think we need to touch that part much"* (M3).

### What they say they want vs what the evidence shows they need

| # | Need | Evidence | Wishlist item it replaces |
|---|---|---|---|
| N1 | **Collect all the documents for a submission in one place, from every channel.** | Colin: *"The slow part is finding the actual documents. They come in from like four different places, broker email, the client portal, sometimes a fax."* Log: *"11 minutes ... to locating all required source documents, compared to an average of 3 minutes to complete the checklist itself."* Log: *"17 of 54 submissions had at least one document arrive through a channel other than the client portal ... each of which took longer to locate."* | Smart autofill (it speeds up the 3-minute part, not the 11-minute part) |
| N2 | **Detect coverage-limit mismatches across documents automatically, with a human confirming each one.** | Log: Anika *"23 were flagged for a coverage-limit mismatch"* out of 61 submissions. Colin: *"Coverage-limit mismatches appeared on 19 of 54."* That is about 36% of all submissions. Colin: *"I have to catch it or it comes back to bite us later."* | AI chat assistant (a chat answers questions; this need is about checking documents) |
| N3 | **Shorten the broker back-and-forth after a mismatch is found.** | Anika: *"What I actually hate is when I have to go back and forth with a broker over email because a document doesn't match ... That can take days waiting on a reply."* Log: *"median 2.1 days, with nine submissions taking longer than 4 days."* | Not on the wishlist at all. This is the largest delay in the data. |
| N4 | **Leave the checklist structure alone.** | Anika: *"Honestly the checklist itself is fine, I've used it forever, I know it cold."* Colin: *"the checklist part goes fast, I basically know it by memory."* Owen agrees. | A new-looking interface (fine as a by-product, but it isn't a need) |

**Where what they say differs from what they need.** Anika's wand answer is *"make the checklist faster to fill out. Some kind of smart autofill."* Two answers earlier, she said the checklist is fine and the broker email loop is what she hates. Her wish is a reasonable guess at a solution, but her own description of the pain points somewhere else. Owen's list repeats her guess, not her pain.

**Mobile access** has no supporting evidence in any of the four materials. I'm deferring it, not rejecting it (see question 4).

### Where the interviews and the usage log agree

**Mismatches are common.** Colin says *"maybe a third of submissions have something off,"* and the log shows 19 of 54 (35%) for him and 23 of 61 (38%) for Anika. His estimate matches the data.

### Where they do not agree

Colin says mismatch-catching *"is not really the bottleneck for me,"* because he *"just reads carefully."* But mismatches show up on 35% of his submissions, and the cost of a mismatch isn't the reading. It's what happens afterwards: Anika's 2.1-day median wait for a broker reply.

Also, nothing in the log measures how many mismatches get *missed*. "I've gotten fast at it" is a statement about speed, not accuracy. Colin's own line, *"it comes back to bite us later,"* suggests that misses do happen.

There is a smaller gap too. Anika's log reports 14 minutes to her first flag, but no time for the checklist itself. Her wish for faster checklist filling can't be checked against her own data.

### Questions for the next round

| # | Question | How the answer changes the design |
|---|---|---|
| Q1 | "When a mismatch slipped past you, what happened, and how often?" (Ask the assistants and Owen.) | **If misses are real and costly** (E&O claims, rework after binding), automatic detection becomes the headline feature and the confirm checkpoint gets stricter. **If misses are rare**, detection drops to a helper and N1 + N3 lead. |
| Q2 | "Walk me through your last broker delay of more than 4 days. What was the broker waiting on?" | **If brokers just lose the email**, structured requests plus automatic reminders are enough. **If they're waiting on the carrier or the client**, the tool needs a status the assistant can see, and possibly a broker-facing upload page, not just better emails. |
| Q3 | "Do all three offices get documents through the same channels? Who receives faxes, and where do they go?" | This decides how intake works: a shared inbox, a fax-to-email gateway, or a per-office setup. If Springfield is portal-heavy, Anika gains less from N1, and the rollout should start in Hartford. |
| Q4 | (To Owen) "What prompted mobile access? Is there a specific moment someone needed it?" | **If it's after-hours approvals**, a narrow mobile view of the bind sign-off is worth building. **If it's a general "nice to have"**, it moves to v2. |

---

## Task 2. Design

**Final designs (Figma):** https://www.figma.com/design/6xILGqurhKPLRyw19t8xMH/Gostride?node-id=31-2  
**Clickable prototype (responsive):** https://ofego.github.io/ajaia-bindflow/prototype/  
**Repo:** https://github.com/Ofego/ajaia-bindflow. It has three screens, with each human checkpoint marked by a purple "Your call" badge.

### User journey (Anika, one submission)

| Step | Today (Bindwise + inbox) | With Bindflow | Evidence |
|---|---|---|---|
| 1. Documents arrive | Hunts through the portal, email and fax | Intake attaches each document to its submission. Low-confidence matches go to her (**checkpoint A**) | N1 · 11 min |
| 2. Checklist | Goes line by line, by memory | Same checklist. Values are already pulled from the documents and shown side by side | N4 · 3 min |
| 3. Mismatch | Reads carefully to spot it | Mismatch highlighted. She confirms it's real (**checkpoint B**) | N2 · ~36% |
| 4. Broker | Writes a free-text email and waits | Structured request drafted. She approves and sends it (**checkpoint C**). The tool chases it and tracks how long it's been | N3 · 2.1 d |
| 5. Bind | Binds in Bindwise | Bind is locked until every flag is resolved. She signs off by name (**checkpoint D**) | Binding definition |

### Screens

1. **Submission queue.** Documents from every channel are grouped by submission, with a status column showing what's missing and what doesn't match. **Checkpoint A:** a fax with an unclear policy number is matched at 71% confidence, so a human confirms it before it's attached. Attaching the wrong client's loss runs is an error the checklist can't catch later.
2. **Reconcile.** The familiar checklist sits on the left. On the right, values are compared across documents, with the mismatch highlighted (application $2M aggregate vs certificate $1M). **Checkpoint B:** the human confirms the mismatch, because the values came from a possibly misread scan, and a false flag costs a 2-day round trip with the broker.
3. **Broker loop & bind.** A drafted request states the exact discrepancy and includes an upload link. **Checkpoint C:** nothing goes to a broker without the assistant's approval, because it's a client relationship. A "waiting on brokers" list brings anything older than 4 days to the top. **Checkpoint D:** the bind button stays disabled until the corrected document has been re-compared and the assistant attests to reviewing every flag. The tool never binds a policy itself.

### Where AI is used, and where it isn't

AI does the extraction, document matching and drafting, the slow mechanical parts. Humans make every decision with consequences: a document attached at low confidence, a mismatch declared real, anything sent outside the company, and the bind itself.

Answering Owen's list:

- **Autofill:** it's here, but as a side effect of reading the documents.
- **The cleaner interface:** delivered.
- **Chat:** replaced with something specific to the job.
- **Mobile:** pending question 4.

---

## Task 3. AI workflow note

- **What I used AI for:**
  - Pulling every numeric claim out of the four materials and cross-checking them against each other.
  - Building the first draft of the evidence table.
  - Generating the HTML prototype from my written screen specs.
  - Drafting the likely objections Owen would raise, so I could rehearse.
- **What I kept human:**
  - Deciding that the broker loop, which isn't on anyone's wishlist, is the biggest cost.
  - Choosing where the four checkpoints go and why.
  - Choosing which wishlist items to defer rather than build.
- **One thing I checked and rejected.** An early AI draft treated Anika's "smart autofill" request as validating Owen's first bullet. I rejected it, because the same transcript shows her pain is the broker loop, and Colin's log puts the checklist at 3 minutes.
- **One thing I checked and corrected.** The AI first wrote a mismatch rate of "about a third" for both assistants. Recomputed, it's 38% for Anika and 35% for Colin, so I cite the exact figures.
