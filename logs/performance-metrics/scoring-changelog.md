# Evolution of Scoring System for Evaluating Model Accuracy

This document tracks revisions to the scoring system used to evaluate model annotation accuracy.


## 11 Nov 2025 – Version 2 (Current)
**Scale:** 0 / 3 / 5  
  - For adult turns:
    - 5 points were given to the correct use of strategy_tags and schema_goals
    - 3 points if some strategy_tags or schema_goal were incorrectly assigned, or if it was unclear whether the tags or schema goal assigned were appropriate
    - 0 points if all tags and schema_goal were incorrect, or if no tags were present
  - For child turns:
    - 5 points were given to the correct assignment of alignment level
    - 3 points if the correctness of the alignment level assigned was ambiguous
    - 0 points if the wrong alignment level was assigned

**Structure:** One  score per adult turn (accounts for strategy tag(s) AND schema goal), one per child turn (alignment level)   
**Rationale:** Increased sensitivity, improved reliability, and finer distinction between “fully correct,” “partially correct,” and “incorrect”  
**Files scored:**
> 36 (1 Bohannon_Bax_gina) first 100.json  
> 48 (3 Brown_Sarah_040028) first 100.json  
> 60 (5 Gelman_2004-Gender_46) first 100.json

**Status:** *Supersedes Version 1*  


---
## 4 Nov 2025 – Version 1
**Scale:** 0 / 0.5 / 1  
  - For adult turns:
    - strategy_tags
      - 1 point was given to the correct use of strategy_tags
      - 0.5 points if one or more tags were incorrect
      - 0 points if all tags were incorrect, or no tags were present
    - schema_goal
      - 1 point was given to the correct tagging of schema_goal
      - 0 points if the incorrect schema goal was assigned
  - For child turns:
    - 1 point was given to the correct assignment of alignment level
    - 0 points if the wrong alignment level was assigned

**Structure:** Two scores per adult turn (one for strategy tags, one for schema goal), one per child turn (alignment level)  
**Purpose:** Initial quantification of model annotation accuracy  
**File scored:**
> 36 (1 Bohannon_Bax_gina) first 100.json → **[Accuracy evaluation 1](https://github.com/wuthree00/LLM-ChildTalk-prompt-engineering/blob/main/logs/performance_metrics/2025-11-04-accuracy-evaluation-1.md)**

**Notes:** Provided results; further discussion revealed the need for finer scoring differentiation
