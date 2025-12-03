# LLM-Based Annotation of Child-Adult Dialogues
> This project explores the use of prompt engineering to benchmark Large Language Model performance (Gemini 2.5 Flash-Lite) on annotating transcriptions of child-adult conversations.
> My role focuses on iteratively refining the annotation prompts and guidelines using real transcripts to improve the model's outputs.  
> The long-term goal is to explore how future supervised fine-tuning (SFT) of the model can improve its recognition of cognitive strategies and learning schemas used by adults when interacting with children.



## About The Project

This repository documents an iterative prompt engineering project that analyses how Large Language Models (LLMs) interpret and annotate child–adult dialogues according to cognitive linguistic guidelines. Using English child-adult conversation data from the CHILDES database, it tracks my experiments, evaluation of model performance, and refinements to both the annotation guidelines and the prompt generation code (in Colab). This work is part of a larger collaboration with PhD students Jing Liu and Siqi Xie.

This work represents one stage of a larger multi-step pipeline. My contribution focuses on developing, testing, and validating the prompt-based annotation process and its outputs. Later stages of the pipeline, including supervised fine-tuning (SFT) of the model, will be carried out by the research team.



### Key Role

*   **Prompt Engineering:** Iteratively designing and refining prompts to improve the model's annotation accuracy and consistency.
*   **Automated Annotation:** Using LLMs to annotate:
    *   Scaffolding strategies, question types, and cognitive schemas in adult utterances.
    *   Cognitive alignment level of a child's response.
*   **Analysis & Comparison:**
    *   Investigating challenges in modelling conversational context.
    *   Comparing annotation consistency across different prompt designs and model parameters.
    


## Repository Structure

This repository is organised to reflect the scientific workflow of the project:

```plaintext
LLM-ChildTalk-prompt-engineering/
├── analyses/
├── experiments/
├── performance-metrics/
├── prompt-refinements/
└── README.md
```

*   **/[analyses](https://github.com/wuthree00/LLM-ChildTalk-prompt-engineering/tree/main/analyses)**: Comparative analyses from multiple experiments, such as model performance across different parameters (eg. temperature) or prompt versions.
*   **/[experiments](https://github.com/wuthree00/LLM-ChildTalk-prompt-engineering/tree/main/experiments)**: Detailed logs for each experimental run. Each file documents the model parameters, the specific prompt used, key excerpts from the raw output, and a qualitative analysis of the model's performance.
*   **/[performance-metrics](https://github.com/wuthree00/LLM-ChildTalk-prompt-engineering/tree/main/performance-metrics)**: Rubrics, scoring methodologies, and quantitative results (eg. accuracy rates) used to formally evaluate model performance.
*   **/[prompt-refinements](https://github.com/wuthree00/LLM-ChildTalk-prompt-engineering/tree/main/prompt-refinements)**: Version-controlled log of all refinements to the prompt engineering process, including:
    *   Guideline refinements: Changes to the original annotation guide (`strategy_annotation_prompt.md`).
    *   Code refinements: Changes to the prompt generation logic in the main Colab notebook.


## Project Status

The first development stage of the English annotation pipeline, which I led, has been completed. Subsequent stages, including supervised fine-tuning (SFT) and additional model evaluation, will be carried out by the research team.

The project as a whole remains under active development, with methodologies, prompts, and analyses continuously being refined.


## Acknowledgments

This research is a collaborative effort with valuable contributions from Linguistics PhD students **[Jing Liu](https://sites.google.com/view/jliucog/home)** and **Siqi Xie**.
