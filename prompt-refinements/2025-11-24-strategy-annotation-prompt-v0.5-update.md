# 24 November 2025 – Post-v0.5 Testing & JSON Update

## Overview

Following the release of **strategy_annotation_prompt_v0.5.md** and the recent updates to the Colab `annotate_dialogue` function, I re-ran all 15 transcripts through the model to validate the new prompt and code changes.  
Test 10 and 11 were conducted on 21 and 24 November 2025 respectively.  
This log documents the testing outcomes, debugging steps, final JSON format updates, and observations about model reliability.  

---
## Summary of Changes 

- Follow-up testing of all 15 transcripts  
- The fixes for `36 (4 Bohannon_Bax_mich) first 100`, `48 (1 Brown_Sarah_040005) first 100` and `60 (4 Brown_Sarah_050030) first 100`   
- Observed model limitations  
- JSON format updates (`score` and mandatory fields)  
- Key takeaways and next steps  

---

## 1. Testing Results for All 15 Transcripts

Note that each transcript contains 100 turns.

In Test 10 (21 Nov 2025), I observed that two files were annotated for **98 turns instead of 100**:  

In Test 11 (24 Nov 2025), I observed that one file was annotated for **98 turns instead of 100**:  

A summary of the transcripts found with incomplete annotation is found below:  

| Test | Date       | File                                  | Annotated Turns| Issue Observed                                                                                                   |
|------|------------|---------------------------------------|----------------|------------------------------------------------------------------------------------------------------------------|
| 10   | 21 Nov 25  | `60 (4 Brown_Sarah_050030) first 100` | 98 / 100       | Hidden character (“Form Feed”) in the file prevented full annotation.                                            |
| 10   | 21 Nov 25  | `36 (4 Bohannon_Bax_mich) first 100`  | 98 / 100       | Extra indentation visible in Notepad could have caused skipped turns.                                            |
| 11   | 24 Nov 25  | `48 (1 Brown_Sarah_040005) first 100` | 98 / 100       | Model failed to annotate all turns initially; resolved by refreshing Colab and re-uploading prompt & transcript. |


### Steps Taken

1. Adjusted token count in Colab step 5.  
2. Re-ran the files multiple times.
3. Refreshed Colab and re-uploaded files before running them again.  
4. Used Gemini to diagnose the problem.  

---

## 2. Bug Fixes & Outcomes

### Test 10 (21 Nov 2025)

Only 98 turns were annotated for the files `60 (4 Brown_Sarah_050030) first 100` and `36 (4 Bohannon_Bax_mich) first 100`  


**2.1 – 60 (4 Brown_Sarah_050030) first 100 Transcript**  

**Original Problem:** 98 turns annotated due to hidden “Form Feed” character.  

**Fix Implemented:** Edited `"what d' you think"` → `"what d'you think"` in the transcript.  

**Gemini Analysis:**  
- The visible change was not the true cause; saving the file in a text editor likely removed the invisible character.  
- Result: **All 100 turns were annotated successfully.**  



**2.2 – 36 (4 Bohannon_Bax_mich) first 100 Transcript**  

**Original Problem:** Turns 91–92 were skipped in the annotation, possibly due to extra indentations.  

**Fix Attempted:** Re-formatted the lines starting from `"toybox"` and re-parsed in Colab.  

**Outcome:** Turns 91-92 remained un-annotated.  
- This suggests residual issues in model processing that may not be directly related to the prompt or formatting.

---

### Test 11 (24 Nov 2025)

This time, files `60 (4 Brown_Sarah_050030) first 100` and `36 (4 Bohannon_Bax_mich) first 100` were annotated for their full 100 turns!  

However, `48 (1 Brown_Sarah_040005) first 100` was only annotated for 98 turns.  


**2.3 – 48 (1 Brown_Sarah_040005) first 100 Transcript**

- Annotated only 98 turns initially, despite running thrice.  
- Solved by refreshing Colab, re-uploading transcript and `strategy_annotation_prompt_v0.5.md`.  
- After fourth attempt: all 100 turns annotated.  

**Observation:** Even with explicit instructions, Gemini occasionally fails to annotate all turns reliably.  
- Error rate observed: 1/15 transcripts (~6.67%) in a single run.

---

## 3. JSON Format Update

Based on these tests, the JSON annotation format was **updated and standardised** to include mandatory `"score"` fields and enforce consistent structure.  

```json
[
  {
   "id": "",
   "metadata": {
      "child_age": "x;xx." //(age;month)
    },
    "dialogue": [
      {
        "turn": 1,
        "speaker": "ADU",
        "utterance": "Dialogue content",
        "annotation": {
          "strategy_tags": ["SubType1_Type1","SubType2_Type2"], // Can be multi-label or empty, where appropriate
          "schema_goal": "A or T or R", // Can be empty, if appropriate
          "score": ""
        }
      },
      {
        "turn": 2,
        "speaker": "CHI",
        "utterance": "Dialogue content",
        "annotation": {
          "alignment_level": "full or partial or disalign or unknown",
          "score": ""
        }
      }
    ]
  }
]


```

### Summary of Mandatory Fields  

This is a summary of the mandatory fields required to be present in the annotation  

| Turn Type | Mandatory Fields                        | Notes                                         |
| --------- | --------------------------------------- | --------------------------------------------- |
| ADU       | `strategy_tags`, `schema_goal`, `score` | Fields must be present even if they are empty |
| CHI       | `alignment_level`, `score`              | Fields must be present even if they are empty |

---

## 4. Key Takeaways

**v0.5 Prompt & Code Improvements**  

* Running transcripts through the updated prompt + revised Colab code improved annotation reliability.  

* All previously failing transcripts were successfully annotated after debugging or refreshing Colab.  


**Model Limitations**  

* Gemini can fail to annotate all turns consistently (~6.67–13.33% of cases).  

* Invisible characters, extra spaces, or wrong indentations could possibly cause the model to skip turns.  


**Importance of JSON Standardisation**  

* Adding explicit instructions on mandatory fields required in the annotation output reduces the possibility of the annotation format not being followed strictly.  

* Ensures consistent processing for all future transcripts.  

---

## 5. Next Steps

Continue testing newly collected transcripts with v0.5 + updated Colab code.  

Monitor and document any skipped turns.  

Explore additional prompt or code adjustments if skipped turns persist.  

Consider implementing automated pre-processing to remove hidden characters or indentation issues before annotation.  

