# 24 Sep 2025

## Refining the Prompt File

**File name**: strategy_annotation_prompt_v0.1.md

These are the notes documenting updates made to strategy_annotation_prompt.md (a file used for LLM-based annotation in dialogues between child and adult)

I made updates to the **strategy annotation prompt** file (**v0.1**) to clarify how strategy tags should be applied, how to better identify specific question types, and to refine the schema goal definitions for **Accretion**, **Tuning**, and **Restructuring**.

---

## Summary of edits made in v0.1

### More detailed instructions on strategy tag application:
* strategy_annotation_prompt_v0.1.md adds explicit instructions on how to apply strategy tags at the utterance level, stating that each unique tag should be used once per utterance, even if mentioned multiple times within that utterance.
* It also provides an example for Information-seeking_Questioning, Instruct_Scaffold, and Explain_Scaffold on how they would be applied to a single utterance.


### Clarification and example for Confirmation Questioning:
* strategy_annotation_prompt_v0.1.md adds a specific example for "Confirmation Questioning" to illustrate its usage: "Do you wanna get some more toys out do you?"


### Examples for Child Utterance Alignment Levels:
* strategy_annotation_prompt_v0.1.md introduces concrete examples for each alignment_level (full, partial, disalign, unknown) for child utterances. These examples help clarify what constitutes each level of alignment.

---

## Detailed Edits

### Overall annotation requirements

**Added:**

> Analyse each turn as a whole at the utterance level and not at the clause level, for example treat “hey bax do you have a spiral like mine let's see it is this yours lookee is this yours i've got one too let's see what color yours is i'll show you what color mine is” as one utterance. Each unique strategy tag should be used once per utterance, even if multiple clauses in that utterance display that tag.
> 
> For instance: “Information-seeking_Questioning” which covers the clauses “hey bax do you have a spiral like mine”, “is this yours”, “lookee is this yours”; the tag “Instruct_Scaffold” which covers the clauses “let's see it”, “let's see what color yours is”; and the tag “Explain_Scaffold” which covers the clauses “i've got one too” and “i'll show you what color mine is”, should appear only once for the first turn like this: ["Information-seeking_Questioning", "Instruct_Scaffold", "Explain_Scaffold"]

The above was added to the description on how to use strategy tags in section **1.1 Strategy Tags (strategy_tags)**

---

### Question type: Confirmation Questioning

**Added:**

> Example:
> "Do you wanna get some more toys out do you?" (this question is seeking confirmation of a stated action with a limited range of expected answers which are yes or no)

The above was added to the criteria for the question tag 'Confirmation Questioning'

---

### Cognitive Alignment Level (of child)

**Added examples to better illustrate the alignment level in the child's response:**

### **Full:**
* Fully aligned; the child completely understands and accepts the information provided by the educator.  
> #### Example 1:  
> ADULT: kittens you see the kittens do you like kittens  
> CHILD: yes i like kittens _(full alignment: child responds directly to the question)_  
> ####  Example 2:  
> ADULT: it's going to be hard to drive over your toys like that why don't you go this way huh  
> CHILD: okay i go this way _(full alignment: child accepts the adult's suggestion)_  
> ADULT: let's see why don't you come back this way bax because there's no toys you can't ride on the toys the car won't go here watch okay  
> CHILD: okay i watch _(full alignment: child agrees to the adult's suggestion to watch)_  
> ADULT: did you all ready play with this toy  
> CHILD: i don’t think so _(full alignment: child responds appropriately to adult's question about whether they have played with the toy)_  

### **Partial:**
* Partially aligned; the child partially understands or accepts the information but has some confusion.  
> #### Example 1:  
> ADULT: is that your favorite car or is that just one of your cars  
> CHILD: my car blue! _(partial alignment: child understands the subject is the car, but not the adult's question about whether the car is their favorite or not)_  
> #### Example 2:
> ADULT: where are you going  
> CHILD: mama go out now _(partial alignment: child understands that the question is about heading somewhere, but appears to think that the adult is asking where the adult is going instead of the child)_  

### **Disalign:**
* Not aligned/cognitive conflict; there is a clear contradiction between the child's understanding and the information provided by the educator.  
> #### Example:  
> ADULT: what color is yours  
> CHILD: mine is blue like sky! _(partial alignment: child understands the question is about the color of the pail, but wrongly identifies their pail as blue instead of green)_  
> ADULT: mine's yellow and yours is what color  
> CHILD: mine is blue, i think _(partial alignment: child understands the question is about the color of the pail, but wrongly identifies their pail as blue instead of green)_  
> ADULT: mine's yellow yours is a different color see this ones yellow and now look look think really hard this is yellow you know this one isn't yellow what color could it be   
> CHILD: maybe it’s blue or green? _(partial alignment: child understands the color is not yellow but is not sure what color it is)_  
> ADULT: it's a color but what color is it green it's green   
> CHILD: green like grass _(partial alignment: child appears to be comparing the color of green to grass. while the child appears to have answered correctly that the pail is green, their following response that it is "yellow like the sun" shows that they did not understand the adult's question)_  
> ADULT: mine's yellow and yours is green see this this is green too see your pail   
> CHILD: mine is yellow like the sun _(disaligned: child was informed that their pail is green but replies that their pail is yellow)_


## Summary
strategy_annotation_prompt_v0.1.md is an updated version that provides more specific guidance and examples for the model, particularly regarding how to apply strategy tags, while more explicitly distinguishing between the levels of cognitive alignment that could be present in the child's response
