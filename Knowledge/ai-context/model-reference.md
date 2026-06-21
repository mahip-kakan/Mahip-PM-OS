# AI Model Reference

*A living reference for the AI/ML concepts and model landscape relevant to my PM work. Update as the space evolves.*

---

## Model Categories (PM-Level Mental Models)

### Large Language Models (LLMs)
**What they do:** Generate, summarize, classify, and transform text.
**PM use cases:** Chatbots, writing assistants, summarization, classification, search.
**Key tradeoffs:** High capability but hallucination risk, latency, and cost at scale.
**When to use:** When the task requires language understanding or generation with nuance.

### Embedding Models
**What they do:** Convert text into numerical vectors for similarity search and retrieval.
**PM use cases:** Semantic search, recommendation systems, deduplication, clustering.
**Key tradeoffs:** Fast and cheap; don't generate text, only compare it.
**When to use:** Retrieval-augmented generation (RAG), powering search features.

### Classification Models
**What they do:** Assign a label to an input (binary or multi-class).
**PM use cases:** Spam detection, sentiment analysis, content moderation, intent routing.
**Key tradeoffs:** Simpler, faster, more predictable than LLMs — but limited to known categories.
**When to use:** When the output space is well-defined and the categories are stable.

### Ranking / Recommendation Models
**What they do:** Score and order items based on predicted user preference.
**PM use cases:** Feed ranking, search relevance, "you might also like," content recommendations.
**Key tradeoffs:** Requires training data; can amplify existing biases.
**When to use:** Personalization, relevance sorting.

### Image / Multimodal Models
**What they do:** Understand or generate images, video, or mixed-modal content.
**PM use cases:** Document parsing, image tagging, visual search, generative media.
**Key tradeoffs:** Data-heavy, computationally expensive, harder to evaluate.
**When to use:** When the core value requires visual understanding or creation.

---

## Key Concepts for AI PMs

### Retrieval-Augmented Generation (RAG)
Combining a retrieval step (find relevant docs) with an LLM generation step. Reduces hallucinations by grounding the model in real documents. Core pattern for knowledge-base Q&A features.

### Grounding
Connecting model outputs to verifiable, real-world data. A grounded answer cites a source. Ungrounded answers are hallucination-prone.

### Hallucination
When a model generates confident, plausible-sounding content that is factually wrong. Rate varies by model, prompt, and domain. Must be accounted for in any user-facing AI feature.

**Mitigation strategies:** RAG, output constraints, human review loops, confidence thresholds, citations, user correction flows.

### Latency Budget
The maximum acceptable response time for an AI feature. LLM calls are slower than traditional API calls. P95 latency (not average) is what users actually experience.

### Evaluation (Evals)
How you measure model quality. Types:
- **Automated evals:** Rule-based or model-graded benchmarks
- **Human evals:** Humans rate model outputs on quality dimensions
- **A/B testing:** Compare model variants on real users and real metrics

Evals must be defined before launch, not after a problem is found.

### Fine-tuning vs. Prompting
- **Prompting (zero/few-shot):** Give the model instructions and examples in the prompt. Fast to iterate, no training required.
- **Fine-tuning:** Train the model on your data to specialize its behavior. Better accuracy on narrow tasks, but expensive and slower to iterate.
- **RAG:** Often a better default than fine-tuning for knowledge-intensive tasks.

### Human-in-the-Loop (HITL)
A design pattern where humans review, approve, or correct AI outputs before they affect real decisions. Essential for high-stakes AI features. Adds latency but reduces risk.

---

## Questions to Ask in Every AI Feature Spec

1. What data does the model need, and do we have it?
2. What's the acceptable latency? (P50, P95)
3. How do we evaluate output quality before launch?
4. What does the failure mode look like, and how do users recover?
5. Is there a human override available?
6. What bias risks exist in the training data or model behavior?
7. What are the data privacy implications of this feature?
8. Does the output need to be explainable to the user?
9. What's the cost per inference at target scale?
10. How does accuracy degrade as input diversity increases?
