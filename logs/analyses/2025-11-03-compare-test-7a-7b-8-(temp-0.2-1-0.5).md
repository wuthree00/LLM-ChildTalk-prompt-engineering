# 3 Nov 2025

## Overview

I compared the output annotations where temperature was **0.2**, **1.0**, and **0.5** again (tests 7a, 7b, and 8 respectively).  
This time, I performed a 2-stage process as documented below.


## Steps Taken

### Stage 1

I fed the following files to **Google AI Studio (Gemini 2.5 Flash Lite):**

- `36 (1 Bohannon_Bax_gina) first 100.json`
- `strategy_annotation_prompt_v0.3.md`
- `2025-10-29-annotation-test-8_36 json_temp 0.5.json`
- `2025-10-28-annotation-test-7b_36 json_temp 1.json`
- `2025-10-28-annotation-test-7a_36 json_temp 0.2.json`

I used this prompt:  
**Prompt used:**
> I analysed "36 (1 Bohannon_Bax_gina) first 100.json" using strategy_annotation_prompt_v0.3.md. I ran this test thrice via Colab using Gemini-2.5 Flash Lite — once with temperature 0.2 (output: 2025-10-28-annotation-test-7a_36 json_temp 0.2.json), once with temperature 1.0 (output: 2025-10-28-annotation-test-7b_36 json_temp 1.json), and once with temperature 0.5 (output: 2025-10-29-annotation-test-8_36 json_temp 0.5.json). Analyse the differences between the three outputs. What are the trends for each output and how could temperature have affected the results and trends for each output? Which one has more accurate tagging based on real human understanding of conversations?

This produced **Output #1** (refer below).

### Stage 2

I then followed up by asking the model to rate the accuracy of each output (temp = 0.2, 0.5, 1) and questioned whether it was sure that temp 0.2 was indeed more accurate than 0.5.

I followed-up with this prompt:  
**Follow-up prompt:**
> How would you rate the accuracy of each one? Are you sure temp 0.2 is the most accurate and not 0.5? Why?

This produced **Output #2** (refer below).

---

## Output #1

### Summary of Findings

Based on a detailed comparison of the three outputs, here’s an analysis of the differences, trends, the impact of temperature, and which output demonstrates more accurate tagging.


### Turn-by-Turn Analysis

**Turn 3 (ADU):** “do you know how to do patty cake”  
- 0.2 & 0.5: `Memory-prompting_Questioning (Schema: T)`  
- 1.0: `Information-seeking_Questioning (Schema: A)`  
→ *Given the context, 0.2’s Memory-prompting_Questioning (T) is more accurate.*

**Turn 11 (ADU):** “mine’s yellow and yours is a different color...”  
- 0.2: `Explain_Scaffold`, `Feedback_Scaffold`, `Thought-provoking_Questioning` (Schema: T)  
- 0.5: Same tags, (Schema: R)  
- 1.0: `Explain_Scaffold`, `Instruct_Scaffold`, `Thought-provoking_Questioning` (Schema: R)  
→ *Restructuring (R) fits better; thus 0.5 and 1.0 are more accurate on schema goal.*

**Turn 19 (ADU):** “yellow um I bet this would go in there”  
- 0.2 & 0.5: `Explain_Scaffold (A)`  
- 1.0: `Explain_Scaffold`, `Instruct_Scaffold (T)`  
→ *Adding Instruct is reasonable; 1.0’s schema (T) may be more fitting.*

**Turn 21 (ADU):** “do you wanna get some more toys out do you do you”  
- 0.2: `Confirmation_Questioning (T)`  
- 0.5 & 1.0: `Information-seeking_Questioning`  
→ *0.2 is more accurate; this is a confirmation, not new information.*

**Turn 41 (ADU):** “let’s see why don’t you come back this way bax...”  
- 0.2: `Instruct_Scaffold`, `Explain_Scaffold`, `Model_Scaffold` (T)  
- 0.5: `Instruct_Scaffold`, `Explain_Scaffold` (T)  
- 1.0: `Instruct_Scaffold`, `Explain_Scaffold`, `Feedback_Scaffold` (T)  
→ *Model_Scaffold at 0.2 fits best (“watch okay”).*

**Turn 47 (ADU):** “can you do patty cake…”  
- 0.2: `Confirmation_Questioning`, `Memory-prompting_Questioning (T)`  
- 0.5 & 1.0: `Confirmation_Questioning (T)`  
→ *0.2’s dual tagging is more complete.*

**Turn 79 (ADU):** “what bax huh oh no he ran over the hat”  
- 0.2 & 0.5: `Information-seeking_Questioning`, `Explain_Scaffold`  
- 1.0: `Explain_Scaffold`, `Social-emotional-support`  
→ *1.0 over-interprets emotion; 0.2/0.5 are more grounded.*

**Turn 92 (CHI):** “my toy is over there”  
- 0.2: `disalign`  
- 0.5 & 1.0: `partial`  
→ *Disalign (0.2) correctly captures the refusal.*

**Turn 98 (CHI):** “my ball!”  
- 0.2: `disalign`  
- 0.5: `partial`  
- 1.0: `unknown`  
→ *All are wrong — should be `full` alignment.*


### Temperature Trends

#### Temperature 0.2 – *Low Determinism*
- **Trend:** More conservative, precise, and exhaustive tagging.  
- **Impact:** Follows definitions closely; consistent and detailed annotations.

#### Temperature 0.5 – *Moderate Determinism*
- **Trend:** Balanced but sometimes omits secondary tags.  
- **Impact:** Minor variability, mostly stable and interpretable.

#### Temperature 1.0 – *High Determinism / Creativity*
- **Trend:** Greater variability, looser definitions, risk of hallucination.  
- **Impact:** Adds unjustified tags (e.g., Social-emotional-support).


### Most Accurate Output

**→ Temperature 0.2** (`2025-10-28-annotation-test-7a_36 json_temp 0.2.json`)

**Reasons:**
1. **Precision & Nuance:** Better distinction between similar strategy types (e.g. Confirmation vs. Information-seeking; Memory-prompting vs. Information-seeking), reflecting a deeper understanding of the adult's intent as per the guidelines.  
3. **Completeness:** Includes multiple valid tags when relevant (e.g. Turn 47 with both Confirmation and Memory-prompting), thus is more comprehensive in identifying all relevant strategies within a single utterance.  
4. **Accurate Alignment:** More accurately distinguishes *disalign* vs *partial* alignment levels in child utterances, particularly when there is a clear contradiction or non-compliance (e.g. Turn 92).  
5. **Definition Adherence:** Fewer questionable or omitted tags used, appearing to follow the specific rules and examples provided in the annotation guide more closely.  


## Output #2

### Accuracy Ratings

| Temperature | File | Accuracy | Rating | Trend |
|--------------|------|-----------|--------|--------|
| **0.2** | `2025-10-28-annotation-test-7a_36 json_temp 0.2.json` | ~90-95% | Very High | Precise, exhaustive, nuanced tagging |
| **0.5** | `2025-10-29-annotation-test-8_36 json_temp 0.5.json` | ~80-85% | High | Balanced but slightly inconsistent |
| **1.0** | `2025-10-28-annotation-test-7b_36 json_temp 1.0.json` | ~70-75% | Moderate | More variable, less precise |


> ### Is Temp 0.2 Really the Most Accurate?

Yes, I am confident that Temperature 0.2 is the most accurate overall, despite 0.5 having one stronger point (Turn 11 schema goal).

Here's a direct comparison highlighting why 0.2 generally edges out 0.5:

### Direct Comparisons Where 0.5 > 0.2
Turn 11 (ADU): "mine's yellow and yours is a different color see this ones yellow and now look look think really hard this is yellow you know this one isn't yellow what color could it be"
- 0.2 Schema Goal: Tuning (T)  
- 0.5 Schema Goal: Restructuring (R)  

Justification: The child incorrectly identified the color multiple times. The adult's utterance directly challenges the child's incorrect understanding ("this one isn't yellow") and guides them to replace it with the correct information ("what color could it be," leading to "green"). This clearly fits the definition of Restructuring (R) which involves challenging or replacing an incorrect idea. Here, 0.5 is more accurate on the schema goal.


### Direct Comparisons Where 0.2 > 0.5

| Turn | Speaker | Key Utterance | 0.2 Tags / Schema | 0.5 Tags / Schema | Justification |
|------|----------|---------------|-------------------|-------------------|----------------|
| 21 | ADU | “do you wanna get some more toys out…” | `Confirmation_Questioning` | `Information-seeking_Questioning` | 0.2 captures intent better |
| 27 | ADU | “oh great” | Schema T | Schema A | Reinforces, not adds — Tuning fits |
| 41 | ADU | “watch okay” | Includes `Model_Scaffold` | Missing `Model_Scaffold` | 0.2 more complete |
| 47 | ADU | “do you know how to do patty cake” | `Confirmation_Questioning`, `Memory-prompting_Questioning` | `Confirmation_Questioning` | 0.2 captures both purposes |
| 53 | ADU | “basketball here toss right here” | Schema T | Schema A | Refining action = Tuning |
| 75 | ADU | “you like the yellow one better don’t you really…” | `Feedback_Scaffold`, `Confirmation_Questioning`, `Instruct_Scaffold` | `Feedback_Scaffold`, `Information-seeking_Questioning`, `Instruct_Scaffold` | 0.2 correctly identifies confirmation phrasing |
| 79 | ADU | “what bax huh oh no he ran over the hat” | Schema T | Schema A | Tuning ongoing understanding |
| 92 | CHI | “my toy is over there” | `disalign` | `partial` | 0.2 captures clear non-compliance |


### Conclusion

> In summary, while **0.5 occasionally makes a better schema goal choice for adults**, **0.2 consistently provides more precise strategy tags, more complete tag sets, and more accurate alignment levels for child utterances across a wider range of turns**. The overall quality and adherence to the detailed guidelines are higher in the 0.2 output.

---

## My Conclusion

Temperature **0.2** consistently yields more **accurate** and **complete** tags for the adult, and more **accurate alignment levels** for child utterances.  
Temperature **0.5** occasionally makes a **more accurate choice in schema goal used by the adult** and has minor omissions but fewer creative deviations.  
Temperature **1.0** introduces unnecessary variability and looser logic.


### Next Steps

* Refine the definition of "Schema Development Goals" (Accretion, Tuning, Restructuring) in strategy_annotation_prompt_v0.3.md to help the model better distinguish between them.
