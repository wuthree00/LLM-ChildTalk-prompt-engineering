# 3 Nov 2025

## Refining the Prompt File

I refined the definition of schema goals in the **strategy annotation prompt** file (v0.3), creating a new version called **strategy_annotation_prompt_v0.4.md**.

The goal is to have the model better understand the distinctions between the schema development goals **Accretion**, **Tuning**, and **Restructuring** when determining the type of schema goals present in the adult’s utterance.

---

## Edits Made

### ACCRETION

**Old:**

> A (Accretion): Adding new information not previously mentioned, attributes, or relationships to the child's existing cognitive schema. This represents the introduction of new knowledge that fits into the existing mental structure.


**New:**

> A (Accretion): Adding new information, attributes, or relationships not previously mentioned to the child's existing cognitive schema. This represents the introduction of new knowledge that fits into the existing mental structure.

> **Example 1:**
> **ADULT: let's learn how to bake today**
> **(Accretion: adult is introducing a new activity which is baking)**

> **Example 2:**
> **ADULT: today we are going to visit my sister, her name is Ruth and you have not met her before. you can call her Aunty Ruth**
> **(Accretion: adult is introducing a new family relationship previously unknown to child)**


---

### TUNING

**Old:**

> T (Tuning): Refining an existing schema by clarifying ambiguities, correcting misunderstandings, or fine-tuning understanding. Corrects, clarifies, or elaborates something already introduced.


**New:**

> T (Tuning): Refining an existing schema by clarifying ambiguities, correcting **minor** misunderstandings, **making an existing skill more precise, or elaborating on an existing concept to** fine-tun**e the child's current** understanding. **This involves making an existing mental structure more precise, functional, or robust.**

> **Example 1:**
> **CHILD: T-R-E-A is the spelling of tree**
> **ADULT: the spelling of tree should be T-R-E-E there is an E at the end and not an A**
> **(Tuning: adult is correcting the child's spelling of the word tree which is an existing word known by the child)**

> **Example 2:**
> **ADULT: do you remember how to do the handstand I taught you last week?**
> **(Tuning: adult is asking about a skill that was previously taught to the child)**

> **Example 3:**
> **ADULT: lets move the soft toy back to the shelf where you took it from**
> **(Tuning: adult is instructing child to move the toy back to its original position known by the child)**


---

### RESTRUCTURING

**Old:**

> R (Restructuring): Completely reorganizing the child's mental schema when there is a fundamental contradiction that requires a significant change in their knowledge structure. Challenges or replaces an incorrect idea.


**New:**

> R (Restructuring): Completely reorganizing **or significantly altering** the child's mental schema when there is a fundamental contradiction, **deeply ingrained misconception, or a need for a major shift in** their **existing** knowledge structure **that renders a previous understanding completely invalid or wrong. This** challenges or replaces an incorrect core idea.

> **Example 1:**
> **(note that adult had already told the child that the child's socks are green)**
> **CHILD: my socks are red**
> **ADULT: actually that color is green and not red, green is the color you see on trees or grass and red is the color of lipstick or blood**
> **(restructuring: adult is trying to correct the child and explain that the color on the child's socks is green and not red as the child thinks, after having mentioned earlier that the socks are green)**
> **CHILD: no my socks are red**

> **Example 2:**
> **CHILD: i am an adult because i am wearing glasses**
> **ADULT: you are not an adult just because you are wearing glasses, children can wear glasses too and not just adults, wearing glasses doesn't make you an adult**
**(Restructuring: adult is correcting the child's wrong concept of how wearing glasses makes one an adult)**
