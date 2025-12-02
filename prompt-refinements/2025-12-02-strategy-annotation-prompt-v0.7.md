# Prompt File Comparison: v0.6 to v0.7

## Aim of Changes & Rationale

The central goal of updating the prompt from v0.6 to v0.7 was to **eliminate "missing" schema goals** (`schema_goal: ""`) when an obvious educational strategy (like a question or instruction) was present.

In v0.6, the prompt contained contradictory and vague rules that led the annotation model to frequently skip the schema goal.

### Examples of What Went Wrong when v0.6 was used:

| Utterance | Tags Found | Problem |
| :--- | :--- | :--- |
| "what color is yours hum" | `["Information-seeking_Questioning"]` | No schema goal was tagged. The model correctly found a strategy, but incorrectly determined there was "no meaningful schema" goal. An Information-seeking question inherently attempts **Accretion (A)** of new knowledge. |
| "whoa got the bear didn't i" | `["Confirmation_Questioning"]` | No schema goal was tagged. A Confirmation question attempts to verify shared knowledge, which is a clear instance of **Tuning (T)** the existing schema. The conflicting rules led to a missed tag. |

### How Changes Were Made to Fix This:

The changes were made to **mandate a direct, non-negotiable link** between the explicit teaching behaviour (`strategy_tags`) and the corresponding cognitive goal (`schema_goal`):

1.  **Prioritisation & Mandate:** The overall instructions were updated to state that assigning strategies is the *first* step, and the schema goal is the *second* step, explicitly requiring a goal if any strategy is found.
2.  **Conflict Removal:** The vague, original exception note in Section 1.2, which caused the model to skip goals, was **deleted**.
3.  **Cross-Reference Enforcement:** A new, simple rule was added to the "Mandatory Fields" section (Section 4) that forces the `schema_goal` to be 'A', 'T', or 'R' any time a strategy is tagged.

---

## Summary of Changes from v0.6 to v0.7

| Section | Change in v0.7 | Aim & Why |
| :--- | :--- | :--- |
| **Overall Annotation Requirements** | **Revised Sentence Structure & Added Mandate:** Explicitly states the order (`first` annotate strategies, `second` determine goal) and adds: "**A Schema Goal is required if any Strategy is present.**" | **Aim:** To clarify the task sequence and mandate the link between the two primary tags. |
| **1.2 Schema Development Goal** | **DELETED: The old "Important note" rule.** (The content was: `"If there are no meaningful strategy tags present and there are no meaningful schemas used in the adult's turn, do not tag the turn with a schema goal, i.e. leave 'schema_goal': empty."`) | **Aim:** To remove the contradictory and ambiguous rule that caused the model to skip annotating turns with the required schema goals. |
| **4. JSON Annotation Format** (Mandatory Fields) | **Added New Mandatory Rule:** `If strategy_tags is NOT empty, schema_goal MUST be 'A', 'T', or 'R'` | **Aim:** To provide a clear, technical constraint that forces the Schema Goal to be assigned whenever an educational Strategy is identified. |
| **5. Annotation Requirements Summary** (Rule 1) | **Replaced old, vague "Completeness" rule with the definitive mandate:** `1. Completeness: Assign a schema_goal (A, T, or R) for every Adult Utterance that is given at least one strategy_tag. The field must be left empty if strategy_tags is empty. Assign an alignment_level (full, partial, disalign, unknown) for every Child Utterance.` | **Aim:** To remove the final instance of the confusing old logic and align the summary section with the new, clear rules established in the preceding sections. |
