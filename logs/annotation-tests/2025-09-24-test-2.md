# Activity Log: 24 Sep 2025

This file describes the second prompt test based on the analysis of results from the [first experiment](https://github.com/wuthree00/LLM-ChildTalk-prompt-engineering/blob/main/logs/2025-09-20-annotation-test.md)

**Description of AI model used**
- **Model**: Gemini 2.5 Flash
- **Settings**:
  - temperature = 1
  - thinking mode = off
  - output length = 65536
  - Top P = 0.95

**Duration:** 241.41 seconds

## Prompt 2
Annotate 36.json based on the strategy_annotation_prompt.md file, analysing each turn as a whole at the utterance level and not at the clause level, for example treat
> "hey bax do you have a spiral like mine let's see it is this yours lookee is this yours i've got one too let's see what color yours is i'll show you what color mine is"
as one utterance that should receive each unique strategy tag once per utterance, even if multiple clauses in that utterance display it

For instance:  
- **Information-seeking_Questioning** → "hey bax do you have a spiral like mine", "is this yours", "lookee is this yours"
- **Instruct_Scaffold** → "let's see it", "let's see what color yours is"
- **Explain_Scaffold** → "i've got one too", "i'll show you what color mine is"

These should appear only once for the first turn.
Note the child is 36 months and may have speech disfluencies based on that age.
Return only the JSON annotation results, in the format required by 'strategy_annotation_prompt.md'.


## Output from Test 2

### Example 1
**Observation:**  
- In Test 2, the model annotated Turn 13 with fewer tags than in Test 1
- Tags used: 'Explain_Scaffold', 'Information-seeking_Questioning'
- Missing tags compared to Test 1: 'Feedback_Scaffold', 'Instruct_Scaffold'

**Analysis:**  
- On a semantic level, Test 2’s output better reflects the exchange: the adult mainly sought information from the child while providing feedback ("it’s a color")


### Example 2
**Problem:**
- The child’s speech in Turn 18 was tagged as having **"full" alignment** instead of **"partial" alignment**.
- The response was only somewhat related to the adult’s utterance.
- Using real-world knowledge, the child’s response "toys" is **disaligned** with the adult’s question about the pail/McDonald’s context.

**Solution:**
- Include this negative example of alignment evaluation in the prompt.
- Specify: *the degree of cognitive alignment of the child’s response "toys" to the adult’s utterance "where did you get this pail at did you eat at mcdonald's and get that it looks like it can you put anything in here look" is **disaligned**, as the child’s answer is irrelevant to the adult’s question.


### Example 3
**Problem:**
- For Turn 21 ("yours is better this is yours though look can you watch this this is musical television hear it bax do you wanna get some more toys out do you do you"), the model reduced tag repetition but **misclassified** the final clause.
- The AI model incorrectly treated "do you wanna get some more toys out do you do you" as two separate clauses when it should be treated as a single meaningful question
- The question above was tagged with 'Information-seeking_Questioning' and 'Confirmation_Questioning', when just the latter would suffice as the answer to this question would simply be 'yes' or 'no'

**Correct tags:**
- 'Social-emotional-support_Scaffold'
- 'Explain_Scaffold'
- 'Instruct_Scaffold'
- 'Confirmation_Questioning'

**Analysis:**
- The clause *"do you wanna get some more toys out do you do you"* should be treated as a **confirmation question**, expecting only *yes/no* answers.


## Next Steps / Solutions
1. Revise 'strategy_annotation_prompt.md' to include explicit **examples** of:
   - Correct handling of alignment levels (partial vs full vs disaligned)
   - Distinguishing 'Confirmation_Questioning' from 'Information-seeking_Questioning'
2. Revise the prompt to instruct the model to apply real-world semantic understanding—for example, recognising references to objects, activities, or places as meaningful entities, rather than treating them as plain strings of text
