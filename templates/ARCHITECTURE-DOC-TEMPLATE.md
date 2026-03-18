# Architecture Document: [System Name]

*Author: Shrish Bajpai | Date: [Date] | Status: Draft*

---

## 1. Context & Purpose

[What is this system? What problem does it solve? Why does the architecture matter?]

## 2. Architecture Overview

[High-level diagram of the system. Show major components and data flow.]

```
[ASCII architecture diagram here]
```

## 3. Architecture Decision Records (ADRs)

### ADR-001: [Decision Title]

**Status:** Accepted
**Date:** [Date]

**Context:** [What is the issue that we're seeing that motivates this decision?]

**Decision:** [What is the change that we're proposing and/or doing?]

**Alternatives Considered:**
- [Alternative A]: rejected because [reason]
- [Alternative B]: rejected because [reason]

**Consequences:**
- [Positive consequence]
- [Negative consequence / trade-off]

**Payment Domain Rationale:** [Why this matters specifically for payments, not just generic "best practice"]

---

### ADR-002: [Decision Title]

[Same structure as above]

---

## 4. Component Design

### [Component 1]
- **Responsibility:** [What it does]
- **Interfaces:** [How other components interact with it]
- **Key Design Choices:** [Notable technical decisions]

### [Component 2]
[Same structure]

## 5. Data Flow

[Describe the key data flows through the system. Include sequence diagrams for critical paths.]

```
[Sequence diagram or flow diagram]
```

## 6. Non-Functional Requirements

| Requirement | Target | Approach |
|-------------|--------|----------|
| Latency | [Target] | [How achieved] |
| Availability | [Target] | [How achieved] |
| Auditability | [Target] | [How achieved] |
| Compliance | [Target] | [How achieved] |

## 7. Failure Modes & Recovery

| Failure | Impact | Detection | Recovery |
|---------|--------|-----------|----------|
| [Failure mode] | [Impact] | [How detected] | [Recovery approach] |

## 8. Future Considerations

[What might change? What would trigger a re-architecture?]
