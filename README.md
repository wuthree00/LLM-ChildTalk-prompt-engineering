# LLM-Based Annotation of Child-Adult Dialogues
> An exploration into using prompt engineering to benchmark Large Language Model performance (Gemini) on annotating the nuances of child-adult interactions.


## About The Project

This repository documents an iterative prompt engineering project that analyzes how Large Language Models (LLMs) interpret and annotate child-adult dialogues according to cognitive linguistic guidelines.

It serves as a record of my work, tracking the experiments conducted, the analysis of model performance, and the refinements made to the annotation prompts. This work is part of a larger collaboration with PhD students Jing Liu and Siqi Xie.


### Key Objectives

*   **Prompt Engineering:** Iteratively designing and refining prompts to improve the model's annotation accuracy and consistency.
*   **Automated Annotation:** Using LLMs to annotate:
    *   Scaffolding strategies and question types in adult utterances.
    *   The cognitive alignment level of a child's response.
*   **Analysis & Comparison:**
    *   Investigating challenges in modelling conversational context.
    *   Comparing annotation consistency across different prompt designs and model parameters.


## Repository Structure

This repository is organised into the following directories:
*   **/experiments**: Contains detailed logs for each experimental run. Each file documents the model parameters, the specific prompt used, key excerpts from the raw output, and a qualitative analysis of the model's performance.
*   **/analyses**: Holds comparative analyses that draw conclusions from multiple experiments, such as comparing model performance across different parameters (eg. temperature) or prompt versions.
*   **/performance-metrics**: Contains the rubrics, scoring methodologies, and quantitative results (eg. accuracy rates) used to formally evaluate model performance.
*   **/prompt-refinements**: A version-controlled history of the master prompt file (`strategy_annotation_prompt.md`). Each entry documents the specific changes made based on the findings from the experiments.


## Project Status

This project is under active development. The methodologies, prompts, and analyses are continuously being refined.


## Acknowledgments

This research is a collaborative effort with valuable contributions from Linguistics PhD students **Jing Liu** and **Siqi Xie**.
