# Memory Integrity Layer

![Memory Integrity Layer](assets/memory-integrity-layer.svg)

## Deterministic Memory Layer for AI Systems

AI systems do not fail only because they hallucinate.

They also fail because they forget, mutate context, mix threads, overwrite decisions, and silently treat temporary assumptions as truth.

**Memory Integrity Layer** separates probabilistic generation from deterministic memory state.

> The model proposes memory.  
> The integrity layer decides what becomes truth.

---

## Core Idea

LLMs can generate useful context, but context is not the same as memory.

Context is temporary.  
Memory is persistent truth.  
Persistent truth requires validation.

Memory Integrity Layer acts as a controlled memory boundary between AI output and stored project state.

No model output should directly mutate memory.

---

## Problem

AI workflows often break because of memory instability:

- silent overwrites
- contradiction with previous decisions
- cross-thread contamination
- assumptions promoted into facts
- lost project constraints
- architecture drift
- stale context reused as current truth

This creates unreliable systems, especially when AI is used for real projects, agents, automation, or code generation.

---

## Solution

Memory Integrity Layer validates every proposed memory update before it becomes persistent state.

It checks:

- existing memory state
- locked decisions
- project constraints
- task scope
- contradiction risk
- confidence level
- approval requirements

Possible outcomes:

- `ACCEPT`
- `REJECT`
- `REQUIRE_HUMAN_APPROVAL`

---

## Architecture

```txt
User / AI Conversation
        ↓
Memory Update Proposal
        ↓
Memory Integrity Layer
        ↓
Validation Engine
        ↓
Conflict Detector
        ↓
Approval Gate
        ↓
Validated Memory State
```

---

## Memory Layers

```txt
Global Memory   → stable system-level rules
Project Memory  → persistent project truth
Task Memory     → active task constraints
Session Memory  → temporary conversation context
```

The system prevents temporary context from becoming permanent memory without validation.

---

## MVP Scope

The first version focuses on a simple file-based memory system:

```txt
INPUT:
memory.state.json + proposed-update.json

OUTPUT:
validation-report.json
```

MVP features:

- structured memory state
- memory update proposals
- locked memory entries
- conflict detection
- validation reports
- human approval flow

---

## Core Principle

```txt
AI can suggest memory.
AI cannot directly write memory.
```

---

## Status

Architecture phase.  
Prototype runtime upcoming.

---

## License

This project is released under a custom source-available license.  
See [`LICENSE`](LICENSE).
