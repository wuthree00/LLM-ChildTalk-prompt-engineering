# 7 Oct 2025 – Qualitative Analysis (Test 3 vs Test 4)

## Description
**Comparison between:** Test 3 and Test 4  
**Focus:** Evaluating qualitative differences in annotation behaviour and tag interpretation  
**Goal:** Determine whether Test 4 shows improved real-world grounding and reduced overtagging compared to Test 3


## Summary of Findings

### Point 1: Tagging in Test 4 More Grounded in Real-World Interpretations
- **Test 3:** Tags often appear based on sentence structure rather than pragmatic meaning.
  Frequent use of multiple overlapping strategy tags (eg. Turn 1 uses `Explain_Scaffold`, `Instruct_Scaffold`, `Information-seeking_Questioning`, `Confirmation_Questioning`) even when contextually redundant.
- **Test 4:** Shows greater restraint – fewer tags per utterance and more selective application (eg. Turn 1 drops `Confirmation_Questioning`; Turn 17 drops `Explain_Scaffold`).
  Tags are now applied where the **pragmatic function** is clearer.

#### Example 1 – Turn 1
* “hey bax do you have a spiral like mine let's see it is this yours lookee is this yours i've got one too let's see what color yours is i'll show you what color mine is”

**Change:** `Confirmation_Questioning` removed → clearer functional scope (adult is exploring, not seeking yes/no confirmation)

#### Example 2 – Turn 10
* “yours is red”

**Change:** Test 3 labels as *partial* alignment; Test 4 labels as *disalign*.  
**Interpretation:** Test 4 is more grounded in real-world meaning: child’s statement contradicts the adult’s prior claim (“mine’s yellow”), showing semantic misalignment rather than incomplete understanding.

#### Example 3 – Turn 13
* “it’s a color but what color is it green it’s green”

**Change:** Overtagging reduced: from three tags (`Feedback_Scaffold`, `Information-seeking_Questioning`, `Explain_Scaffold`) in Test 3 to two in Test 4 (`Thought-provoking_Questioning`, `Explain_Scaffold`).  
**Interpretation:** Reflects better conceptual matching: the adult corrects *and* encourages reasoning, rather than merely seeking information.

#### Example 4 – Turn 17
* “where did you get this pail at did you eat at mcdonald's and get that it looks like it can you put anything in here look”

**Change:** Test 3 used (`Information-seeking_Questioning`, `Confirmation_Questioning`, `Explain_Scaffold`, `Instruct_Scaffold`); Test 4 drops `Explain_Scaffold`.  
**Interpretation:** Aligns with function: a series of questions + instruction, and not explanation.


#### Example 5 – Turn 25
* “boom”

**Change:** Tag changed from `Explain_Scaffold` to `Model_Scaffold`.  
**Interpretation:** Although the earlier misclassification was corrected from being an explanation, the rightful classification might not be “boom” either.


### Point 2: Improved Evaluation of Alignment
- **Test 3:** Contains many “partial” alignments where the model interprets the child’s response as only loosely related (eg. Turns 8, 10, 12, 14).
- **Test 4:** Refines these boundaries – some “partial”s become “disalign” (eg. Turn 10) or “full” (Turn 14).
- **Interpretation:** Evaluation now depends more on **semantic fit** and **communicative intent** rather than surface structure alone.
- **Conclusion:** The model in Test 4 shows progress toward **real-world meaning grounding**, consistent with the revised prompt.


### Point 3: Overcorrection of Tagging in Test 4
- **Turn 33:**
  > “whoa got the bear didn’t i”
  - Test 3: `Confirmation_Questioning`
  - Test 4: `Confirmation_Questioning`, `Explain_Scaffold`
  - The added `Explain_Scaffold` is unnecessary but not severely incorrect; arguably acceptable within interpretive bounds.


### Point 4: Hypothesis on Alignment Patterns
**Hypothesis:** Including a string of *partially-aligned* examples before a *disaligned* one might have taught the model that disalignment must follow partial alignment.
However, Test 4 data shows some evidence that indicates room for disproving this hypothesis.

**Findings:**
- Turn 16 (child) is `disalign`, following Turn 14 (`full`) → disproves dependency
- Turn 32 (`disalign`) follows Turns 24 (`partial`), 26 (`full`), 28 (`full`) → again disproves dependency
- Turns 34-42: `partial`, `partial`, `full`, `partial`, `disalign` → confirms independence
- Turns 74-78: `full`, `full`, `disalign` → further confirms that partial alignment does **not** have to precede disalignment


### Point 5: Wrong Tagging Persists Across Both Tests
Some tagging errors remain consistent in both versions.

#### Example – Turn 18
* “toys”

- **Tagged as:** “Full” alignment in both tests
- **Issue:** Should be “Partial” – the response is tangentially related to the adult’s question (“where did you get this pail…”)


### Point 6: Numbering and Reference Errors
Both tests show misreferenced turns, though for different utterances.

| Turn | Test 3 | Test 4 | Correct |
|------|---------|---------|---------|
| 14 | “green like grass” *(wrong)* | “green!” *(correct)* | Test 4 correct |
| 16 | “my pail yellow too!” *(correct)* | “mine is yellow like the sun” *(wrong)* | Test 3 correct |

**Observation:** 
Both models misidentified different turns but the misquoted lines do exist elsewhere in the transcript. The assigning of the wrong utterances to the wrong number was not due to hallucinations, but seemingly due to the same line appearing elsewhere within the same transcript.


## Overall Interpretation
**Test 4 demonstrates:**
- Greater restraint and contextual grounding in tagging
- Improved semantic evaluation of child–adult alignment
- Persistent but isolated numbering errors
- A tendency to overcorrect and overuse tags

**Conclusion:**
Enabling *thinking mode* and refining the annotation prompt led to more pragmatically accurate, real-world grounded tagging behaviour.
