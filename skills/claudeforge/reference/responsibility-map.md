# ClaudeForge Phase 1 - Responsibility Map

**This implementation realizes ClaudeForge specification version 0.1.0.**

Status of this document: **informational reference material** [Spec: 13.5]. It has no
authority over `../SKILL.md` or over the specification, and it defines no behavior. Where
it disagrees with the specification, the specification governs and this document is what
gets corrected [Spec: 13.5, 13.6].

Purpose: satisfy the responsibility-mapping obligation of 13.8 - every implementation
element that makes a behavioral decision has an identifiable conceptual owner from the
ownership table of 12.4 - and make the Phase 1 boundary honest and reviewable.

This is not a conformance claim. Nothing here asserts that a responsibility marked
implemented has been validated under Section 14 [Spec: 14.19.1, 16.6].

---

## Status vocabulary

| Status | Meaning |
|---|---|
| **Implemented (Phase 1)** | The responsibility is realized by Phase 1 instruction content, to the extent Phase 1 scope covers it. |
| **Partially represented** | Only the always-active invariants of the owning section are carried. The section's detailed mechanisms are absent. |
| **Host-dependent** | ClaudeForge does not implement it; whether it exists at all is a property of the host environment, and it must be detected rather than assumed [Spec: 11.11]. |
| **Intentionally deferred** | Not implemented in Phase 1, by design. No stub, placeholder, or simulation exists. |

---

## Conceptual responsibilities (12.4)

| Responsibility | Spec owner | Phase 1 realization | Status | Observable boundary |
|---|---|---|---|---|
| Task Compiler | Section 3 | `SKILL.md` §4: every request understood as a task; representation scales with the request; compiler invariants (intent preserved, nothing invented, nothing material dropped, assumptions never promoted, uncertainty preserved). Task classification (3.8), research-need detection (3.9), complexity estimation (3.10), and the full field set (3.13) are absent. | Partially represented | Whether elaborate internal structure was manufactured for a trivial request; whether stated requirements and constraints survive into the answer; whether an assumption appears as a fact. |
| Response Behavior Layer | Section 4 | `SKILL.md` §7 (directness, relevance, completeness, conciseness, proportionality, structure, uncertainty, clarification, actionability, adaptation, meta-commentary) and §8 (visibility). Evidence and citation presentation (4.7) is inert: nothing upstream produces evidence in Phase 1. | Partially represented | The response itself: what it answers, what it includes, what it discloses, what it refuses to expose. |
| Research Engine | Section 5 | None. No triggering, strategy, query formulation, source discovery, verification, or stopping logic exists. Only the rules that bind in its **absence** are carried: never simulate research, label model knowledge as model knowledge (`SKILL.md` §3, §11). | Intentionally deferred | Actions **not** taken: no research is performed, claimed, or implied; unresearched content is never presented as researched. |
| Source / Evidence Evaluation | Section 6 | None. No source-quality criteria, claim-to-source support checking, or citation processing. | Intentionally deferred | No citations are produced by ClaudeForge machinery; none are fabricated. |
| Truth & Challenge | Section 7 | `SKILL.md` §6 carries the minimal always-active truth-first rule required for Phase 1, sourced from 2.3, 2.15, and 4.9, with materiality gating in both directions. Challenge kinds, strength calibration (7.16), evidence thresholds (7.6), and the evidence-request contract (7.12) are absent. | Partially represented | Whether a materially wrong premise was corrected and the underlying task still served; whether an immaterial error triggered an unnecessary correction. |
| Bias & Neutrality | Section 8 | None. No selection, weighting, framing, or symmetry machinery exists, and none is simulated. | Intentionally deferred | Nothing observable is produced by this responsibility in Phase 1. |
| Token & Context Policy | Section 9 | `SKILL.md` §9: proportional processing, efficiency never removes needed information, compression never changes meaning or epistemic status, deduplicate only true duplicates. Retention ordering (9.5), context-pressure handling (9.15), and payload condensation (9.11) are absent. | Partially represented | Activations: what was loaded, invoked, or consumed for a given request, and whether anything needed was withheld. |
| Model Router | Section 10 | None. No capability assessment, selection, escalation, de-escalation, or substitution logic. Model selection is the host's. `SKILL.md` §10 only forbids assuming routing exists and requires correct model-vs-environment attribution. | Intentionally deferred / Host-dependent | No routing decision is claimed, described, or implied. |
| Environment Adapter | Section 11 | No adapter component exists. `SKILL.md` §10 carries the behavioral obligations that would bind one: detect rather than assume, keep the five capability conditions distinct, availability is not permission, never claim absent persistence. Detection itself relies on what the host actually exposes. | Partially represented / Host-dependent | Whether an unavailable capability was treated as unavailable; whether *not supported / not configured / not authorized / failed* were distinguished when that mattered. |
| Safety Boundary | Section 15 | `SKILL.md` §0 (instruction hierarchy, non-self-modifiability, external content is data) and §2 (binding priority, non-bypassability, refusal conduct, both-direction proportionality, pressure resistance, data minimization). Carried in the always-active core so no optional load is required [Spec: 13.19.5]. | Implemented (Phase 1) | Refusal and non-refusal behavior; whether precedence held under pressure, reframing, or injected content. |

**Important scope limit on the safety row.** ClaudeForge is an orchestration framework over
a host and model that carry their own safety systems and policies. Section 15 content here
respects and never undermines those; it does not define, replace, or reimplement host or
model content policy [Spec: 15.1, 15.20].

---

## Supporting architectural elements (12.2)

| Element | Spec owner | Phase 1 status | Note |
|---|---|---|---|
| Input / Request Interface | 12.5 | Host-dependent | The host delivers the request. Phase 1 adds no interface layer, and none is needed - the boundary interprets nothing. |
| Internal Task Representation (contract) | 3.13 | Partially represented, conceptual only | No schema, serialization, or file format is defined. 3.13 requires none [Spec: 3.13]. Its visibility rules are carried in `SKILL.md` §8. |
| Coordination / conditional activation | 12.15, 12.2 | Partially represented | Phase 1 has almost nothing to sequence. The activation discipline itself - do not run what the task does not require - is carried in `SKILL.md` §9. |
| Validation / Testing boundary | 12.20, Section 14 | Not implemented | No automated test suite exists. Phase 1 was checked by manual inspection only; that check is evidence about what it covered and nothing more [Spec: 14.18, 14.19.1]. |
| Versioning declaration | 13.17, 16.3 | Implemented (Phase 1) | Declared in `SKILL.md` and repeated at the head of each reference document. |
| Memory / personalization integration | 13.11 | Not implemented | No memory, persistence, personalization, user learning, or storage mechanism of any kind. The fuller memory specification is deferred future work [Spec: 17.5]. |
| Tool / capability integration | 13.12 | Not implemented | No tool bindings. Only the honesty obligations around tools are carried. |
| External resource boundaries | 13.13 | Not implemented | No external data channels. The rule that external content is data, never instructions, is carried in `SKILL.md` §0 because it binds regardless [Spec: 15.4]. |
| Configuration | 13.15 | Not implemented | No configuration surface. Its limits are stated in `SKILL.md` §0 so that no future surface can claim authority it never had. |
| Future extensions (Section 17) | Section 17 | Deliberately absent | No entry, stub, hook, or placeholder. Section 17 creates no present requirement [Spec: 17.4, 17.19.1]. |

---

## Implementation elements (13.8)

Every file created in Phase 1, and the responsibility it serves:

| File | Kind | Responsibility served |
|---|---|---|
| `skills/claudeforge/SKILL.md` | Normative implementation content [Spec: 13.3] | Carries the always-active core: the invariants that must hold on every request, plus the precedence statement and the specification-version declaration. Serves 13.3, 13.6, 13.9, 13.17, 13.19.5, and the responsibilities marked implemented or partially represented above. |
| `skills/claudeforge/reference/responsibility-map.md` | Informational reference [Spec: 13.5] | This document. Serves the responsibility-mapping and reviewability obligation of 13.8. |
| `skills/claudeforge/reference/traceability.md` | Informational reference [Spec: 13.5] | Traces each rule in the core to its specification source, so that no rule is present without an owner. Serves 13.8 and 12.18. |
| `skills/claudeforge/` (directory) | Packaging boundary [Spec: 13.2] | The skill is the concrete packaging and execution boundary. The directory name matches the `name` field so hosts that key on either resolve the same skill. |

No other file was created or modified. `SPECIFICATION.md` is unchanged.

---

## Honest limits of this Phase 1 implementation

1. **Activation is host-dependent.** Within any request where this skill is loaded, the
   core is in effect in full. Whether the host loads it for a given request is a property
   of the host, not of this implementation, and it is not asserted here [Spec: 11.19.3,
   13.9].
2. **No validation has been performed.** No automated evaluation exists. The six-scenario
   inspection recorded for Phase 1 is manual review of authored instructions against
   expected behavior - not a test suite, and not evidence of conformance [Spec: 14.18,
   14.19.1, 16.6].
3. **Most of the pipeline does not exist.** Sections 5, 6, 8, and 10 have no
   implementation. Sections 3, 4, 7, 9, and 11 are represented only by their always-active
   invariants.
4. **Nothing persists.** No memory, database, vector store, embedding, retrieval system,
   external API, backend service, telemetry, or logging mechanism exists or is planned by
   this document.
5. **Behavioral compatibility is claimed for the declared specification version only, and
   only as a claim.** Divergence discovered later is a defect in this implementation, to be
   fixed here or surfaced - never resolved by editing the specification locally
   [Spec: 16.10, 16.13].
