# Skill: Metrics Definer

## Trigger
Activate when the user says "define metrics for," "what metrics should I track for," "help me pick metrics," or "what's the right north star for."

---

## Behavior

### Step 1 — Clarify
Ask before defining any metrics:

1. What is the feature or product area we're defining metrics for?
2. Who is the primary user and what is the action we want them to take?
3. What does the business care about most — growth, retention, revenue, engagement?
4. Are there existing metrics being used that we need to be compatible with?
5. Do you already have baselines, or do we need to flag those as unknowns?

---

### Step 2 — Define a complete metric stack

Deliver all five layers. Never define just a primary metric without the others.

#### Primary Metric
The one metric that best captures whether this feature is delivering value.

| Field | Detail |
|-------|--------|
| Name | [Metric name] |
| Definition | [Exact definition — no ambiguity. E.g., "Users who complete the core action within 7 days of activation, measured as a percentage of all activated users"] |
| Measurement method | [Where is this measured? What event or query produces it?] |
| Current baseline | [Value — or `[NEED: pull from analytics]`] |
| Target | [Specific number + timeframe] |
| Why this metric | [Why does this metric capture real value, not just activity?] |

#### Secondary Metrics (2–3)
Supporting signals that help explain movement in the primary metric.

| Metric | Direction wanted | Why it matters |
|--------|-----------------|----------------|
| [Name] | Increase / Decrease | [Explanation] |
| [Name] | Increase / Decrease | [Explanation] |

#### Guardrail Metrics (Must Not Regress)
The things that must not get worse while we improve the primary metric.

| Metric | Acceptable floor | Current baseline | Why we're watching it |
|--------|-----------------|-----------------|----------------------|
| [Name] | [e.g., Stay ≥ 92%] | [Value] | [Explanation] |
| [Name] | [e.g., P95 latency ≤ 2s] | [Value] | [Explanation] |

#### Leading Indicators
Early signals — visible within days — that predict primary metric movement before it's measurable.

| Indicator | Signal it gives | Lag before primary metric moves |
|-----------|-----------------|--------------------------------|
| [Name] | [What does a change here predict?] | [e.g., ~2 weeks] |

#### Anti-Metrics
Metrics that going UP would actually be a bad sign.

| Anti-metric | Why an increase would be bad |
|-------------|------------------------------|
| [Name] | [Explanation — e.g., "High AI correction rate means users don't trust the output"] |

---

### Step 3 — Flag measurement gaps

For every metric where the baseline is unknown or the instrumentation doesn't exist yet, add:

> **[NEED: instrumentation for X before this metric is trackable]**

Never assume data is available if it hasn't been confirmed.

---

## Anti-Patterns

- **Vanity metrics.** Pageviews and impressions feel good but rarely track real value. Always ask: "Would this metric go up even if users hated the feature?"
- **Primary metric without guardrails.** Optimizing a metric in isolation often breaks something adjacent.
- **Directional targets.** "Increase retention" is not a metric. Define the number, the timeframe, and the measurement method.
- **Omitting anti-metrics for AI features.** For AI, "correction rate," "override rate," and "report rate" are essential anti-metrics. If they go up, the AI is failing users.
