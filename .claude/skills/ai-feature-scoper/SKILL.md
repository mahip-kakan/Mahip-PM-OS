# Skill: AI Feature Scoper

## Trigger
Activate when the user says "scope this AI feature," "help me spec an AI feature," "I want to add AI to [product area]," or "what do I need to think through for [AI idea]."

---

## Purpose
AI features require a different scoping process than standard product features. This skill ensures you've answered the questions that determine whether an AI feature is technically feasible, user-trustworthy, and safe to ship — before you write a single user story.

---

## Behavior

### Step 1 — Understand the idea
Ask:
1. What is the user problem we're solving with AI? (Not "we want to add AI" — what pain does it address?)
2. What type of AI capability does this require? (Generation / Classification / Ranking / Search / Multimodal / Other)
3. Who are the users, and how often will they interact with the AI output?
4. What does good output look like? What does bad output look like?
5. Is the output advisory (user decides what to do) or automated (system acts on the output)?

---

### Step 2 — Produce an AI Feature Scope Document

#### 1. Problem Framing
| Field | Detail |
|-------|--------|
| User problem | [What problem does the AI solve? Not "add AI" — the underlying user pain] |
| Why AI, not rules/code | [What makes this problem require ML rather than a deterministic solution?] |
| User action without AI | [What does the user do today as a workaround?] |

---

#### 2. AI Capability Definition
| Field | Detail |
|-------|--------|
| Model type | [LLM / Classifier / Ranker / Embedding / Multimodal — pick the right tool] |
| Input | [What data goes in: format, source, freshness requirements] |
| Output | [What the model returns: format, structure, constraints on length or content] |
| Model options | [Existing models that could work — open source, API, or build in-house] |
| Build vs. buy | [Recommendation with rationale] |

---

#### 3. Data Requirements
| Field | Detail |
|-------|--------|
| Training data needed | [Volume, format, labeling requirements — or N/A if using pre-trained model] |
| Data we have | [What's available internally] |
| Data gaps | [What we'd need to collect, buy, or generate — flag as risk if significant] |
| Data privacy | [Does this feature process PII? What data handling rules apply?] |
| Data freshness | [How stale can the model's knowledge be before it hurts UX?] |

---

#### 4. Evaluation Strategy
*You must define how you'll measure model quality before you build. "We'll know it when we see it" is not a strategy.*

| Evaluation type | Method | Target threshold |
|-----------------|--------|-----------------|
| Accuracy / quality | [Human evals / automated benchmark / task completion rate] | [Minimum acceptable score] |
| Latency | [P50 / P95 measurement] | [Max acceptable: Xs P95] |
| Hallucination rate | [How are you detecting incorrect outputs?] | [Max acceptable rate] |
| Bias audit | [What bias dimensions are relevant? How will you test?] | [Pass/fail criteria] |

---

#### 5. Failure Modes (Required Section)
*What happens when the AI is wrong? This must be answered before shipping any AI feature.*

| Failure mode | Likelihood | User impact | Detection method | Recovery path |
|--------------|------------|-------------|-----------------|--------------|
| [e.g., Hallucinated fact in output] | Med | High | [User reports / automated checks] | [User can edit / flag / override] |
| [e.g., Biased output for user segment] | Low | High | [Bias monitoring] | [Human review queue] |
| [e.g., Latency spike degrades experience] | Low | Med | [Latency monitoring] | [Graceful fallback to non-AI path] |

---

#### 6. Human Override Design (Required for Any User-Facing AI)
| Question | Answer |
|----------|--------|
| Can the user see the AI's output before it takes effect? | Yes / No |
| Can the user edit or reject the output? | Yes / No — if No, justify |
| Can the user report a bad output? | Yes / No |
| Is there a non-AI fallback path? | Yes / No — if No, what's the risk? |
| Who reviews escalated AI failures? | [Process] |

---

#### 7. Trust and Transparency Design
| Question | Answer |
|----------|--------|
| Does the user know they're interacting with AI? | Yes / No — if No, is that intentional and appropriate? |
| Does the AI explain its reasoning? | Yes / No — [when is explanation necessary?] |
| Does the AI show confidence levels? | Yes / No |
| Are limitations communicated to users? | [How?] |

---

#### 8. Ethical Risk Assessment
| Risk | Applies? | Mitigation |
|------|----------|------------|
| Output bias against protected groups | Yes / No | [How mitigated] |
| Privacy risk from processing user data | Yes / No | [How mitigated] |
| Potential for misuse or manipulation | Yes / No | [How mitigated] |
| Regulatory / compliance exposure | Yes / No | [Which regulation, how addressed] |

---

#### 9. Metrics for AI Quality (in Production)
These must be instrumented before launch:

| Metric | Definition | Acceptable range |
|--------|------------|-----------------|
| Override rate | % of AI outputs the user manually changes | [Target: < X%] |
| Correction rate | % of outputs flagged as wrong | [Target: < X%] |
| Engagement rate | % of users who act on AI output | [Target: > X%] |
| Latency P95 | 95th percentile response time | [Target: < Xs] |

---

#### 10. Go / No-Go Criteria for AI Feature Launch
| Criterion | Threshold | Status |
|-----------|-----------|--------|
| Accuracy above minimum threshold | [X%] | [ ] |
| Latency within budget | [< Xs P95] | [ ] |
| Hallucination rate below maximum | [< X%] | [ ] |
| Human override mechanism implemented | Required | [ ] |
| Bias audit complete | Required | [ ] |
| Failure modes documented and mitigated | Required | [ ] |
| Privacy review complete | Required | [ ] |

---

## Anti-Patterns for AI Features

- **"Let's just use GPT-4 for everything."** Model choice should follow from requirements, not default to the most popular option.
- **Shipping without evals.** If you don't know what good looks like before launch, you won't know if you've launched something bad.
- **No override mechanism.** Users must be able to correct AI mistakes. This is not optional.
- **Hiding that it's AI.** Transparency builds trust. Deception destroys it — and creates legal exposure.
- **Evaluating only the happy path.** Test edge cases, adversarial inputs, and underrepresented user segments.
- **Confusing AI capability with product decision.** Just because the model can do something doesn't mean we should let it.
