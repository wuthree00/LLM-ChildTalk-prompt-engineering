# LLM-Based Annotation of Child-Adult Dialogues
> An exploration into using prompt engineering to benchmark Large Language Model performance (Gemini) on annotating the nuances of child-adult interactions.


## About The Project

This repository documents an iterative prompt engineering project that analyses how Large Language Models (LLMs) interpret and annotate child-adult dialogues according to cognitive linguistic guidelines.

It serves as a record of my work, tracking the experiments conducted, the analysis of model performance, and the refinements made to the annotation guidelines and the prompt generation code. This work is part of a larger collaboration with PhD students Jing Liu and Siqi Xie.


### Key Objectives

*   **Prompt Engineering:** Iteratively designing and refining prompts to improve the model's annotation accuracy and consistency.
*   **Automated Annotation:** Using LLMs to annotate:
    *   Scaffolding strategies and question types in adult utterances.
    *   The cognitive alignment level of a child's response.
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

*   **/[analyses](https://github.com/wuthree00/LLM-ChildTalk-prompt-engineering/tree/main/analyses)**: Holds comparative analyses that draw conclusions from multiple experiments, such as comparing model performance across different parameters (eg. temperature) or prompt versions.
*   **/[experiments](https://github.com/wuthree00/LLM-ChildTalk-prompt-engineering/tree/main/experiments)**: Contains detailed logs for each experimental run. Each file documents the model parameters, the specific prompt used, key excerpts from the raw output, and a qualitative analysis of the model's performance.
*   **/[performance-metrics](https://github.com/wuthree00/LLM-ChildTalk-prompt-engineering/tree/main/performance-metrics)**: Contains the rubrics, scoring methodologies, and quantitative results (eg. accuracy rates) used to formally evaluate model performance.
*   **/[prompt-refinements](https://github.com/wuthree00/LLM-ChildTalk-prompt-engineering/tree/main/prompt-refinements)**: A version-controlled log of all refinements made to the prompt engineering process. This includes documentation for:
    *   Guideline Refinements: Changes to the master annotation guide (`strategy_annotation_prompt.md`).
    *   Code Refinements: Changes to the prompt generation logic within the main Colab notebook.


## Project Status

This project is under active development. The methodologies, prompts, and analyses are continuously being refined.


## Acknowledgments

This research is a collaborative effort with valuable contributions from Linguistics PhD students **[Jing Liu](https://sites.google.com/view/jliucog/home)** and **Siqi Xie**.
