# 27 Sep 2025 — Test 3

## Description
**Settings:** Gemini 2.5 Flash
**Temperature:** 1
**Thinking mode:** Off
**Output length:** 65,536
**Top P:** 0.95

Files used: 36.json; strategy_annotation_prompt_v0.1.md  
Output JSON file: 2025-09-27-annotation-test-3_36.json

### Prompt 3
Annotate `36.json` based on the `strategy_annotation_prompt_v0.1.md` file, thereafter generating a JSON file as the output. Note the child is 36 months and may have speech disfluencies based on that age. When analysing the dialogue, interpret utterances not only at the textual level but also in terms of real-world meaning — for example, recognise contextual references like people, objects, activities, and places in everyday life.

### Note that:
- I edited the **strategy annotation prompt itself**, rather than the prompt keyed into Google AI Studio.

### Differences in test 3 (compared to test 2)
- Instructions to use each strategy tag once per turn was moved from the prompt itself to "strategy_annotation_prompt_v0.1.md" under the **“Strategy Tags”** heading.
  - Includes the instruction to analyse each turn at the utterance level (i.e. as a whole turn) and not at the clause level.
- Examples of cognitive alignment in child speech (full, partial, disaligned) were moved to "strategy_annotation_prompt_v0.1.md" under the **Cognitive Alignment Level** heading.
  - In strategy_annotation_prompt_v0.1.md under **2.1 Cognitive Alignment Level** which indicates the degree of cognitive alignment of the child's utterance with the adult's previous turn, I provided example sentences from the 36.json transcript of **aligned**, **disaligned**, **partially aligned**, to provide with more specific instances from the real world.
- Added example to differentiate “Information-seeking_Questioning” and “Confirmation_Questioning” under **Questioning Type** 

### New Prompt (Simplified and Cleaner)
Annotate `36.json` based on the `strategy_annotation_prompt_v0.1.md` file, thereafter generating a JSON file as the output. Note the child is 36 months and may have speech disfluencies based on that age. When analysing the dialogue, interpret utterances not only at the textual level but also in terms of real-world meaning, for example recognise contextual references like people, objects, activities, and places in everyday life.

## OUTPUT from Test 3

### Example 1
- An additional tag **“Feedback_Scaffold”** was used in *Turn 13* for Test 3 but not in Test 2.
- `schema_goal` was deemed as **T** rather than **A** (in Test 2), which is more accurate as the adult is fine-tuning the child’s understanding.
→ **Hypothesis:** The instruction to “interpret utterances…in terms of real-world meaning” helped the model tag utterances based on semantic meaning rather than syntax.

### Example 2
- *Turn 18* is still marked as having **“full” alignment** rather than **“partial”** — no improvement from Test 2 despite examples of alignment levels being provided.

### Example 3
- The **“Confirmation_Questioning”** tag is now used instead of **“Information-seeking_Questioning”**.
→ Possibly due to this example being explicitly stated in `strategy_annotation_prompt_v0.1.md` as a **Confirmation Questioning** type.

To do: Check if other confirmation-questioning examples were correctly tagged this time (compare results of Test 3 vs Test 2).
