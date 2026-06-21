# Skill: Launch Checklist

## Trigger
Activate when the user says "create a launch checklist," "launch checklist for [feature]," "pre-launch checklist," or "what do I need to do before launching [X]."

---

## Behavior

### Step 1 — Calibrate to risk level
Ask:
1. What are we launching? (Feature, product, API, AI capability)
2. Who is the audience? (Internal / select users / full user base / new market)
3. What's the rollout plan? (Gradual / flag-gated / full launch)
4. What's the single biggest risk you're worried about?
5. Is this reversible? (Can we roll back in under 30 minutes if something goes wrong?)

Risk level = High if: full user base, irreversible, or AI feature with user-visible outputs.
Risk level = Medium if: gradual rollout, flag-gated, or limited audience.
Risk level = Low if: internal, easily reversible, small scope.

---

### Step 2 — Generate checklist by phase

#### Pre-Launch (T-2 weeks)
- [ ] Success metrics defined with baselines and targets
- [ ] Rollback plan documented and tested
- [ ] All Must-have requirements verified complete
- [ ] Analytics instrumentation deployed and tested in staging
- [ ] Feature flag configured (if flag-gated rollout)
- [ ] Monitoring dashboards set up for key metrics
- [ ] Legal / compliance review complete (if applicable)
- [ ] Privacy review complete (if user data involved)
- [ ] [HIGH RISK ONLY] Load testing completed at 2x expected traffic

#### Pre-Launch (T-1 week)
- [ ] Go/no-go criteria documented and shared with decision owner
- [ ] Internal announcement drafted
- [ ] External announcement / release notes drafted (if public launch)
- [ ] Support team briefed on what's changing and what to expect
- [ ] Customer success briefed (if enterprise product)
- [ ] On-call rotation confirmed for launch window
- [ ] [AI FEATURE] Human review or escalation path defined for failure modes
- [ ] [AI FEATURE] Model evaluation results reviewed and signed off

#### Launch Day
- [ ] Deploy during low-traffic window (confirm: [time])
- [ ] Monitor for first 2 hours post-launch — who's on watch?
- [ ] P0 bug response protocol confirmed — who decides to roll back?
- [ ] Send internal announcement
- [ ] Send external announcement (if applicable)
- [ ] Log launch timestamp

#### Post-Launch (T+1 week)
- [ ] Review primary metric vs. target
- [ ] Review all guardrail metrics — any regressions?
- [ ] Check support ticket volume for new patterns
- [ ] [AI FEATURE] Review override/correction rate — is the AI performing as expected?
- [ ] Write post-launch summary with what worked and what didn't
- [ ] Archive project if work is complete

---

### Step 3 — Assign owners

For each checklist item, prompt the user:
"Who owns this item, and by when does it need to be done?"

Do not deliver a checklist with no owners — a checklist without owners is a wishlist.

---

## Rollback Plan (Required for High-Risk Launches)

If not already documented, ask the user to fill in:

- **Rollback trigger:** [What metric or signal causes a rollback call?]
- **Rollback decision owner:** [Name — one person, not a committee]
- **Rollback steps:** [Step-by-step — fast enough to execute in under 30 minutes]
- **Rollback verification:** [How do you confirm the rollback was successful?]
