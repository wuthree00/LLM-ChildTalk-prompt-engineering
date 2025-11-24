# 24 Nov 2025 – Accuracy Evaluation (v0.5 Output Scoring)

## Overview
**Aim**: To quantify the model’s annotation accuracy output generated using the updated prompt file **strategy_annotation_prompt_v0.5.md**, using the updated (0, 3, 5) scoring system.

**How**:  

* Three transcripts were selected for detailed scoring. Each turn was evaluated according to the 0/3/5 rubric introduced in [version 2](https://github.com/wuthree00/LLM-ChildTalk-prompt-engineering/blob/main/performance-metrics/scoring-changelog.md#11-nov-2025--version-2-current).  

* The purpose of this evaluation is to measure whether prompt v0.5 leads to improved alignment with the annotation guidelines, building on the methodology used earlier in *[4 Nov 2025 – Quantifying Accuracy Rate of Output](https://github.com/wuthree00/LLM-ChildTalk-prompt-engineering/blob/main/performance-metrics/2025-11-04-accuracy-evaluation-1.md)*.

For relevant prior details about [changes made](https://github.com/wuthree00/LLM-ChildTalk-prompt-engineering/blob/main/prompt-refinements/2025-11-19-strategy-annotation-prompt-v0.5.md) in strategy_annotation_prompt_v0.5, corrections to the Python code in [Colab](https://github.com/wuthree00/LLM-ChildTalk-prompt-engineering/blob/main/prompt-refinements/2025-11-20-colab-prompt-logic-refinement.md), or [further debugging](https://github.com/wuthree00/LLM-ChildTalk-prompt-engineering/blob/main/prompt-refinements/2025-11-24-strategy-annotation-prompt-v0.5-update.md) to fix the outputs using v0.5 in tests 10 and 11, refer to relevant aforementioned documents.

The three evaluated transcripts using v0.5 as the input file achieved an **average accuracy of 82.6%**, indicating a clear improvement from outputs generated with the v0.4 file (77.4%).

---

## Detailed Methodology
For clarity, this evaluation focuses specifically on **scoring the model-annotated outputs**, and does not repeat the refinements done to strategy_annotation_prompt_v0.5.md, the Python code in Colab, or further debugging after evaluating earlier outputs.  

Steps performed for scoring:

1. Three of the annotated JSON files generated using strategy_annotation_prompt_v0.5.md were manually reviewed.  
2. Each adult turn was scored according to the (0, 3, 5) scale for:  
   - `strategy_tags`  
   - `schema_goal`  
3. Each child turn was scored according to the same scale for:  
   - `alignment_level`  
4. Total possible points for each transcript were calculated, and percentage accuracy was derived.  
5. A comparison table between **v0.4** and **v0.5** accuracy rates was created to measure improvement.

---

## Scoring Rubric (0 / 3 / 5 System)

For clarity, this rubric was used to evaluate the accuracy of the model's output in annotating the transcripts.

Note that this latest scoring replaced the earlier 0 / 0.5 / 1 rubric used in the 4 November 2025 scoring.  

For the scoring changelog, see *[scoring-changelog.md](https://github.com/wuthree00/LLM-ChildTalk-prompt-engineering/blob/main/performance-metrics/scoring-changelog.md)*.

**General Rules:**
- **5 points** — Fully correct  
- **3 points** — Partially correct with some errors  
- **0 points** — Incorrect or missing annotation  

The annotations considered were:  
- `strategy_tags` [ADULT]
- `schema_goal` [ADULT]
- `alignment_level` [CHILD]

---

## Results: Accuracy Scores (v0.5)
### **Transcript-level accuracy (%)**
| Transcript                             | v0.4      | v0.5      |
|----------------------------------------|-----------|-----------|
| 36 (1 Bohannon_Bax_gina) first 100     | 78.2%     | **80.6%** |
| 48 (3 Brown_Sarah_040028) first 100    | 78%       | **88%**   |
| 60 (5 Gelman_2004-Gender_46) first 100 | 76%       | **79.2%** |
| **Average**                            | **77.4%** | **82.6%** |

**Observation:**  
All three transcripts show improved accuracy under v0.5, with the strongest increase seen in `48 (3 Brown_Sarah_040028)`.

---

## Distribution of Tag Accuracy
The following table shows a breakdown of how often the model produced **correct** (5), **partially correct** (3), or **incorrect** (0) tags.

### **Breakdown of Tags per Category (%)** (v0.5)
| Transcript                   | Wrong (0)| Partial (3)| Correct (5)|
|------------------------------|----------|------------|------------|
| 36 (1 Bohannon_Bax_gina)     | 11%      | 21%        | 67%        |
| 48 (3 Brown_Sarah_040028)    | 6%       | 15%        | 79%        |
| 60 (5 Gelman_2004-Gender_46) | 16%      | 12%        | 72%        |

For comparison, the breakdown in tag accuracy for v0.4 is show below

### **Breakdown of Tags per Category (%)** (v0.4)
| Transcript                   | Wrong (0) | Partial (3) | Correct (5) |
|------------------------------|-----------|-------------|-------------|
| 36 (1 Bohannon_Bax_gina)     | 13%       | 22%         | 64%         |
| 48 (3 Brown_Sarah_040028)    | 16%       | 15%         | 69%         |
| 60 (5 Gelman_2004-Gender_46) | 18%       | 15%         | 67%         |


**Interpretation:**  
- A higher proportion of **correct** tags appears consistently across all files.  
- `48 (3 Brown_Sarah_040028)` stands out with the lowest error rate (6%).  
- The relatively small proportion of partial/correct errors suggests stronger adherence to prompt guidelines after the v0.5 revision.

---

## Evaluation
Overall, **prompt v0.5 led to improved alignment with the strategy-annotation guidelines**, reflected in:
- Higher accuracy percentages across all evaluated transcripts  
- Reduced number of incorrect or missing tags  
- More consistent differentiation between partial and full correctness  

Improvements are consistent across transcripts, suggesting that the gains stem from the prompt revision rather than transcript-specific quirks. These findings reinforce that the refinements made to the prompt and annotation criteria were effective.

---

If you want, I can also auto-generate the GitHub front-matter block (title, date, tags) to match the format of your repo.
