# 4 Nov 2025 – Quantifying Accuracy Rate of Output

## Overview
**Aim**: To evaluate the model's accuracy in annotating the dialogue between child and adult.  

**How**: 15 files containing the first 100 turns of each conversational dialogue were run through the model **Gemini 2.5 Flash Lite** in Colab, using the prompt file `strategy_annotation_prompt_v0.4.md`.  

The **temperature** was set to 0.2, based on prior evaluation in [test 9](https://github.com/wuthree00/LLM-ChildTalk-prompt-engineering/blob/main/logs/annotation-tests/2025-11-03-test-9.md), which gave the most accurate output.  

I manually validated the model's annotations based on the prompt guidelines and my linguistic knowledge. Each annotation was scored as 0, 0.5, or 1 (see below for scoring criteria).  

The file `36 (1 Bohannon_Bax_gina) first 100_annotated.json` had an **accuracy rate of 77.6%**



## Detailed Methodology
1. For the first conversation between the 36-month-old and the adult, I created a file containing the first 100 turns of the transcript `Eng-NA/Bohannon_Bax_gina.clean` → **Resulting file:** `36 (1 Bohannon_Bax_gina) first 100.json`.  
2. The same process was applied to other adult-child conversations, totaling **15 conversations** (5 conversations per age group).  
3. Each conversation was run through Colab (model = Gemini 2.5 Flash Lite) using **temperature 0.2** and the prompt file `strategy_annotation_prompt_v0.4.md`, aiming for an **80% accuracy rate**.  
4. Notations were made in the output file:  '36 (1 Bohannon_Bax_gina) first 100_annotated_20251104022641 (temp 0.2).json'
5. The accuracy rate of the model was **tabulated** in a Google Sheets document `LLM childtalk measuring accuracy rate`

## Rubric for Quantifying Accuracy Rate
Each adult utterance was scored on two components: strategy_tags and schema_goal  
Each child utterance was scored on one component: alignment_level  


**Adult turns:**  
Strategy_tags:
- **1 point** for correct use of `strategy_tags`  
- **0.5 points** if one or more tags were incorrect  
- **0 points** if all tags were incorrect or missing

Schema_goal:
- **1 point** for correct tagging of `schema_goal`  
- **0 points** if the incorrect `schema_goal` was assigned   



**Child turns:**  
Alignment_level:
- **1 point** for correct assignment of `alignment_level`  
- **0 points** if the wrong alignment level was assigned
