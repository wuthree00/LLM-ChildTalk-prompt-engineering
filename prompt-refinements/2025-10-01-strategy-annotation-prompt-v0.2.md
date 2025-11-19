# 1 Oct 2025

## Refining the Prompt File

**File name**: strategy_annotation_prompt_v0.2.md

I refined the **strategy annotation prompt** file (**v0.2**) to improve the clarity of examples provided under the **“Disalign”** category in **Section 2.1 – Cognitive Alignment Level (alignment_level)**.  

The changes aim to prevent the model from inferring that disalignment must occur after several instances of partial alignment.

---

## Edits Made

### DISALIGN CATEGORY

**Changes made to examples:**
- Removed the first half of the exchange that included several examples of **partial alignment** before the example of **disalignment**, to  avoid the possibility of the model inferring that disalignment must occur after several instances of partial alignment

**Old example:**

> ADULT: what color is yours  
> CHILD: mine is blue like sky! *(partial alignment: child understands the question is about the color of the pail, but wrongly identifies their pail as blue instead of green)*  
> ADULT: mine's yellow and yours is what color  
> CHILD: mine is blue, i think *(partial alignment: child understands the question is about the color of the pail, but wrongly identifies their pail as blue instead of green)*  
> ADULT: mine's yellow yours is a different color see this ones yellow and now look look think really hard this is yellow you know this one isn't yellow what color could it be  
> CHILD: maybe it’s blue or green? *(partial alignment: child understands the color is not yellow but is not sure what color it is)*  
> ADULT: it's a color but what color is it green it's green  
> CHILD: green like grass *(partial alignment: child appears to be comparing the color of green to grass. while the child appears to have answered correctly that the pail is green, their following response that it is "yellow like the sun" shows that they did not understand the adult's question)*  
> ADULT: mine's yellow and yours is green see this this is green too see your pail  
> CHILD: mine is yellow like the sun *(disaligned: child was informed that their pail is green but replies that their pail is yellow)*

**New example:**

> ADULT: mine's yellow and yours is green see this this is green too see your pail  
> CHILD: mine is yellow like the sun *(disaligned: child was informed that their pail is green but replies that their pail is yellow)*
