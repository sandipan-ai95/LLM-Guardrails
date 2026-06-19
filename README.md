# LLM Guardrails with LiteLLM

A production-ready implementation of **LLM Guardrails** using **LiteLLM** for safety, validation, observability, and reliability across multiple Large Language Models (OpenAI, Anthropic, Gemini, Azure, Ollama, etc.).

---

## Overview

As organizations adopt LLMs in production, several bottlenecks emerge:

- Prompt injection attacks
- Sensitive data leakage
- Hallucinated outputs
- Toxic or harmful content
- Schema inconsistencies
- Cost explosions
- Rate limit failures
- Multi-model fallback complexity

This project demonstrates how to implement **Guardrails** on top of **LiteLLM** to solve these problems.

LiteLLM acts as a unified gateway for all LLM providers while guardrails add validation and safety layers.

---

## Architecture

User Input
↓
Pre-Guardrails
↓
LiteLLM Proxy
↓
LLM Provider
↓
Post-Guardrails
↓
Validated Response

### Guardrail Layers:

### 1. Input Guardrails
Before sending prompts to the model:

- Prompt injection detection
- Jailbreak detection
- PII masking
- Toxicity filtering
- Rate limiting
- Length validation

---

### 2. Runtime Guardrails

During inference:

- Timeout protection
- Model fallback
- Cost tracking
- Token budgeting
- Retry strategies

---

### 3. Output Guardrails

After generation:

- JSON schema validation
- Hallucination checks
- Toxicity scanning
- Compliance validation
- Citation verification
- Red-team policy checks

---

## Why LiteLLM?

LiteLLM provides:

- Unified API for 100+ LLMs
- Automatic fallback routing
- Cost tracking
- Caching
- Logging
- Load balancing
- Retry handling

Without changing business logic.

Example:

```python
from litellm import completion

response = completion(
    model="gpt-4o",
    messages=[{"role": "user", "content": "Hello"}]
)
