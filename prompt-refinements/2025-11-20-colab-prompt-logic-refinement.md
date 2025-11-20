# 20 November 2025

## Engineering: Refining the Prompt Generation Code in Colab

**This log documents changes made directly to the Python code in the Colab notebook, specifically within the `annotate_dialogue` function. The `strategy_annotation_prompt.md` guideline file was not altered.**

I performed a significant overhaul of the `full_prompt` logic within the `annotate_dialogue` function. The previous prompt structure contained critical factual errors and inefficiencies that impacted model performance. The new prompt architecture is designed to be more robust, clear, and accurate.

During testing, I observed that the model occasionally skipped turns in the dialogue. A subsequent hotfix was implemented directly into the prompt string to address this specific issue.

### Key Changes Implemented in the Code

1.  **Resolved Critical Factual Error:** Removed the hardcoded, incorrect child's age ("60 months old") from the prompt string to prevent factual contradictions with the source data.

2.  **Implemented a Structured Prompt Architecture:** Replaced the previous single-paragraph instruction with a clear, multi-section format within the Python f-string. This includes a persona-setting command, a "Key focus areas" list, and distinct sections for the annotation guide and dialogue data.

3.  **Enforced Annotation Completeness (Hotfix):** After observing that the model occasionally skipped turns, I added an explicit instruction (`Do not skip any turns in the transcript.`) directly into the prompt string to ensure every line of the dialogue is processed.

4.  **Cleaned Prompt Logic:** Eliminated redundant and confusing text fragments from the old prompt string to provide the model with a clean, unambiguous set of instructions.

This comprehensive update to the prompt generation code is expected to lead to more reliable, complete, and consistent JSON outputs from the model.

---

### **Before: Old Code in `annotate_dialogue`**

```python
# The old prompt was a single f-string with a hardcoded, incorrect age and messy formatting.
full_prompt = f'''
annotation guide:{prompt_guide}\n\n
Annotate all turns in the excerpts based on the annotation guide, thereafter generating a JSON file as the output. Note that the child is 60 months old and may have speech disfluencies typical of that age. ...etc... : ---\n{prompt_data_string}
'''
```
---

### **After: New Code in `annotate_dialogue`**

```python
# The new prompt is a structured f-string, is factually correct, and includes the completeness instruction.
full_prompt = f'''
You are an expert in educational cognitive development, as defined in the annotation guide provided below.
Your task is to meticulously annotate all turns in the following dialogue excerpt. You must strictly adhere to every rule, definition, and example within the annotation guide. Do not skip any turns in the transcript.
Be mindful of typical speech patterns and cognitive abilities for this age.
Key focus areas:
  1. **Avoid Over-tagging:** Assign only strategy_tags that are clearly evidenced by the utterance’s communicative intent.
  2. **Schema Goals:** Pay special attention to distinguishing A (Accretion) from T (Tuning), and only tag R (Restructuring) when there is an explicit and direct reorganisation of the child’s understanding.
  3. **Output Format:** Your entire output must be ONLY the valid JSON object, perfectly matching the structure specified in the guide. Do not add any conversational text, explanations, or markdown formatting before or after the JSON.
---
**ANNOTATION GUIDE:**
{prompt_guide}
---
**DIALOGUE TO ANNOTATE:**
{prompt_data_string}
'''
```
