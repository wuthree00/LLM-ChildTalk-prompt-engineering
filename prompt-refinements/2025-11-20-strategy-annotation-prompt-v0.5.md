# 19 Nov 2025

## Refining the Prompt File

**File name**: strategy_annotation_prompt_v0.5.md

I made major changes to the **strategy annotation prompt** file (**v0.4**) to improve the accuracy, clarity, and consistency of the model's annotations. This new version, **strategy_annotation_prompt_v0.5.md**, resolves critical contradictions in tagging methodology, enhances schema goal definitions based on established learning theories, and introduces explicit rules for handling non-meaningful conversational turns.

---

### Key Issues Identified in Previous Outputs

*   **Errors:** Some files contained repeated tags within the same turn (eg. turns 3 and 5 in `36 (2 Bohannon_Bax_karen) first 100_annotated_20251104022735 (temp 0.2).json`). Additionally, turns with non-meaningful content (eg. "Oh okay" in turn 49) were incorrectly assigned strategy tags and schema goals.

---

### Summary of Changes in v0.5

*   **Resolved Critical Contradiction:** Modified the instructions in Section 3.1 to provide a clear methodology for utterance-level tagging, resolving a conflict with Section 1.1 that likely caused repeated tags in outputs generated with v0.4.
*   **Enhanced Schema Goal Definitions:** Expanded the definitions for Accretion, Tuning, and Restructuring with more detailed explanations and added a summary paragraph explicitly contrasting the three modes of learning, based on *Accretion, Tuning, and Restructuring: Three Modes of Learning (Rumelhart & Norman, 1978)*.
*   **Added Explicit Rules for Non-Meaningful Turns:**
    *   Introduced an "Important note" in Section 1.1 to prevent the tagging of conversational fillers (eg. “Uh huh”, “Okay”).
    *   Added a corresponding rule in Section 1.2 to leave the `schema_goal` field empty if `strategy_tags` is empty.
*   **Refined Core Definitions and Instructions:**
    *   Emphasized that each unique tag should appear only once per turn.
    *   Sharpened the definitions for several scaffolding and questioning tags for greater clarity.
    *   Clarified that the list of “Common Multi-Strategy Combinations” is non-exhaustive.
*   **Updated JSON Format:** Added a `"score": ""` field to the JSON structure to support quantitative evaluation of model performance.
*   **General Cleanup:** Improved overall readability and removed extraneous text.

---

## Detailed Changelog: v0.4 vs. v0.5

| Section | v0.4 | v0.5 |
| :--- | :--- | :--- |
| **Overall Annotation Requirements**| As an expert in educational cognitive development, please provide complete annotations for the child-educator dialogue. For Adult Utterances (ADU), annotate the educational strategies and schema development goals. For Child Utterances (CHI), annotate the degree of alignment. | As an expert in educational cognitive development, please provide complete annotations for the child-educator dialogue. For Adult Utterances (ADU), annotate the educational strategies and schema development goals **used by the adult**. For Child Utterances (CHI), annotate the degree of alignment **in the child's utterance**. |
| **1.1 Strategy Tags** | Analyse each turn as a whole at the utterance level and not at the clause level, for example treat “hey bax do you have a spiral like mine let's see it is this yours lookee is this yours i've got one too let's see what color yours is i'll show you what color mine is” as one utterance. Each unique strategy tag should be used once per utterance, even if multiple clauses in that utterance display that tag... | Analyse each turn as a whole at the utterance level and not at the clause level, for example treat “hey bax do you have a spiral like mine let's see it is this yours lookee is this yours i've got one too let's see what color yours is i'll show you what color mine is” as one **turn**. Each unique strategy tag should **only appear once per turn**, even if multiple clauses within the same turn could be reflected by that strategy tag... **This same tagging criteria applies for all the strategy tags.** <!-- note that this portion was added in v0.1 and refined in v0.5 --> |
| **1.1 Scaffold Type (Feedback)** | ...Do not use this tag for rhetorical fillers, or neutral follow-up comments that do not seek to confirm the correctness of new information, point out deviation in details, or reinforce logic after restructuring. | ...Do not use this tag for rhetorical fillers, or neutral follow-up comments that do not seek to confirm the correctness of new information, point out deviation in details, reinforce logic after restructuring, **or function to nurture the child**. |
| **1.1 Scaffold Type (Explain)** | Explain: Provide detailed information, reasons, or descriptions of features. | Explain: Provide detailed information, reasons, descriptions of features, **or clarifications**. |
| **1.1 Scaffold Type (Model)** | Applicable for: Demonstrating examples of new behaviors, showing refined operations, modeling cross-schema transfer. | Applicable for: Demonstrating examples of new behaviors **or skills**, showing refined operations, modeling cross-schema transfer. |
| **1.1 Scaffold Type (Social-emotional-support)**| Social-emotional-support: Responses involving emotions and motivation. | Social-emotional-support: Responses involving emotions and **providing** motivation. |
| **1.1 Scaffold Type**| *non-existent* | **Important note: If a turn consists of only a rhetorical filler... do not annotate that turn with any strategy tag. Leave the strategy_tags field empty...** |
| **1.1 Scaffold Type**| Note on how to differentiate between Guided-completion Questioning and Confirmation Questioning: | *This incomplete instruction was removed.* |
| **1.1 Questioning Type (Information-seeking)**| Characteristics: ... (3) The purpose is to obtain new information. | Characteristics: ... (3) The purpose is to **elicit** new information **from the child, not just to confirm information the speaker already presumes to be true.** |
| **1.1 Questioning Type (Memory-prompting)**| *non-existent* | **Example: "Remember when your shirt got torn"...** |
| **1.1 Questioning Type (Confirmation)**| Seeks confirmation of known or presumed information... | Seeks confirmation **or disconfirmation** of known or presumed information... |
| **1.1 Questioning Type (Guided-completion)**| ...The purpose is to guide the child's active participation. | ...The purpose is to guide the child's active **thinking or use of their own judgment to determine the next step or possible answers.** |
| **1.2 Schema Development Goal (Accretion)** | ...This represents the introduction of new knowledge that fits into the existing mental structure. | ...This represents the introduction of new knowledge... **No structural changes in the information-processing system takes place as the existing knowledge base is merely incremented by a new set of facts.** |
| **1.2 Schema Development Goal (Tuning)** | ...This involves making an existing mental structure more precise, functional, or robust. | **...Beyond merely adding to the mental database,** this type of learning involves **continual fine-tuning or minor modifications to** make the existing mental structure more precise, functional, or robust. |
| **1.2 Schema Development Goal**| *non-existent* | **Crucially, there are the differences between A, T, and R...** <br><br> **Important note: If there are no meaningful strategy tags present... do not tag the turn with a schema goal, i.e. leave "schema_goal": empty.** |
| **3.1 Clause-level Strategy Annotation**| ### 3.1 Clause-level Strategy Annotation (Important): <br> 1. Each educator utterance may contain multiple clauses, and each clause must have at least one strategy annotation... | ### 3.1 Method for Annotating Complex Utterances: <br> **To accurately determine the final list of utterance-level tags as required in Section 1.1...** <br> **1. Step 1: Identify Clauses...** <br> **2. Step 2: Analyze Each Clause...** <br> **3. Step 3: Consolidate and De-duplicate...** |
| **3.2 Common Multi-Strategy Combinations**| *non-existent* | **Note: The example combinations provided are non-exhaustive.** |
| **4. JSON Annotation Format**| `"strategy_tags": [...] // Can be multi-label` <br> `"schema_goal": "A or T or R"` | `"strategy_tags": [...] // Can be multi-label or empty, where appropriate` <br> `"schema_goal": "A or T or R", // Can be empty, if appropriate` <br> `"score": ""` |
| **5. Annotation Requirements Summary**| 1. Completeness: Ensure all three schema development goals (A, T, R) are included in the annotations. | 1. Completeness: Ensure all three schema development goals (A, T, R) are included in the annotations, **unless there are no meaningful strategy tags present and there are no meaningful schemas used in the adult's utterance.** |
