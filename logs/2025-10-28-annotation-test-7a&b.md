## 28 Oct 2025 – Tests 7a & 7b

### **Settings**
- **Environment:** Google Colab  
- **Model:** Gemini 2.5 Flash Lite  
- **Files used:** `strategy_annotation_prompt_v0.3.md`, `36 (1 Bohannon_Bax_gina)_first100.json`  
- **Temperature:**  
  - **Test 7a:** 0.2  
  - **Test 7b:** 1.0  

### **Prompt (in Colab)**
Annotate all turns in the excerpts based on the annotation guide, thereafter generating a JSON file as the output. Note that the child is 36 months old and may have speech disfluencies typical of that age. When analysing the dialogue, interpret utterances not only at the textual level but also in terms of real-world meaning (eg. people, objects, activities, places). Return only the annotation results in valid JSON format, following the structure specified in the guideline file. When analysing, avoid over-tagging: assign only those `strategy_tags` that are clearly evidenced by the utterance’s communicative intent. Pay special attention to distinguishing **A (adding new information)** from **T (refining an existing idea)**, and tag **R** only when the adult explicitly reorganises the child’s understanding.

### **Goal**
To test how temperature affects annotation behaviour, consistency, and diversity when using the same model and prompt.

### **Outputs**
- `2025-10-28-annotation-test-7a_36 json_temp 0.2.json`  
- `2025-10-28-annotation-test-7b_36 json_temp 1.json`  

### **Summary of Observed Differences**

| **Dimension** | **Test 7a (temp 0.2)** | **Test 7b (temp 1.0)** | **Trend** |
|:--|:--|:--|:--|
| **Consistency / Determinism** | Very consistent; repetitive use of the same tag combinations (eg. `Explain_Scaffold + Information-seeking_Questioning`) | More variable and flexible; strategy mixes change across similar utterances | ↑ Creative diversity, ↓ consistency |
| **Tag breadth** | Narrower tag set; high reuse of scaffolding tags, minimal experimentation | Broader repertoire (adds `Social-emotional-support`, `Guided-completion_Questioning`, mixes unexpected pairs) | ↑ Diversity of strategy tags |
| **Schema goal distribution** | Strong bias toward **T (Tuning)** & **A (Accretion)** | More distributed; introduces **R (Restructuring)** and alternation between **A** & **T** | ↑ Contextual flexibility, ↓ goal rigidity |
| **Confidence level** | “Safe” predictions — avoids rare or uncertain categories | Willing to assign low-confidence or novel categories (eg. `unknown`) | ↑ Exploration, ↓ certainty |
| **Alignment annotations** | Binary (mostly `disalign`) | More nuanced (`partial`, `unknown`) | ↑ Gradient interpretation |

### **Detailed Analysis**
**Temperature 0.2:** Produced more precise and deterministic outputs, closely following guideline definitions. It consistently identified finer-grained distinctions such as `Memory-prompting_Questioning`, `Confirmation_Questioning`, and `Feedback_Scaffold` when clearly justified. Schema goals leaned heavily toward **T (Tuning)**, suggesting a conservative bias toward refinement of existing knowledge.

**Temperature 1.0:** Produced more exploratory and interpretive outputs. Strategy tags varied more (eg. added `Thought-provoking_Questioning` and `Social-emotional-support`), and schema goals alternated more evenly between **A (Accretion)** and **T (Tuning)**, with occasional **R (Restructuring)**. Alignment annotations were softer, often `partial` or `unknown`.

### **Interpretation of Temperature Effects**
- **Lower Temperature (0.2):** Encourages deterministic behaviour → more precise, rule-adherent, and reproducible annotations.  
- **Higher Temperature (1.0):** Increases randomness → more diverse and contextually imaginative but less consistent results.  

### **Note**
Portions of this analysis were assisted by ChatGPT (GPT-5) to systematically compare the two model outputs and summarise observed trends across annotation dimensions.
