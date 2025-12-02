## Strategy Annotation Prompt Version 0.6 Updates

This document tracks changes from `strategy_annotation_prompt_v0.5.md` to `strategy_annotation_prompt_v0.6.md`.


## Summary of Changes

The primary goal of this update is to clarify the criteria for applying strategic tags to **Adult Utterances (ADU)**. This version specifically addresses the problem of numerous conversational turns being incorrectly left unannotated due to overly narrow definitions in the previous version.

*   **Problem with v0.5:** Random checks of the annotated dataset found numerous instances where the model failed to apply **any** `strategy_tags` or `schema_goal` to valid, content-bearing Adult Utterances (ADU). Turns like "hi sarah," "must be nice to be small enough to walk under tables," and "that'll last about one day" were left with empty annotation fields.
*   **Possible Cause:** v0.5 contained overly narrow definitions for existing tags and a broad instruction to exclude any utterance that "does not add any meaningful content," leading the model to treat conversational moves as unannotated filler.
*   **This version aims to prevent the over-exclusion of meaningful Adult Utterances by clarifying the boundary between non-annotated, purely mechanical filler sounds and essential strategic tags.**


### 1. Updated Definition for `Social-emotional-support_Scaffold`

The criteria for applying the `Social-emotional-support_Scaffold` tag have been expanded to explicitly include the **initiation/maintenance of social interaction**.

| Section | Change Type | Old Text Snippet | New Text Snippet |
| :--- | :--- | :--- | :--- |
| **1.1 Strategy Tags: Social-emotional-support** (Definition) | **Modified** | *Tag only when the utterance aims to regulate emotion, provide reassurance, or build rapport (eg. “That’s okay”, “Don’t worry, try again”). Do not tag short acknowledgements (“okay”, “yeah”) which could be interpreted as placeholders, unless they clearly soothe or encourage emotionally.* | *Tag utterances that aim to regulate emotion, provide reassurance, **initiate/maintain social interaction (greetings, eg. "Good morning", "Have a good rest" or "See you tomorrow")**, or clearly encourage (eg. "Good job", "You did your best" or "Don't worry, try again"). Do not tag short, non-emotional backchanneling sounds (eg. "Uh huh", "Mhm" or "Oh") or comments that appear to indicate agreement but have a neutral function as they do not provide emotional support or motivation, such as "Yeah" or "Okay."* |

### 2. Revised Exclusionary Rules (Removed Redundancy)

The redundant illustrative examples were removed, and the core exclusionary rule was emphasized to align with the expanded `Social-emotional-support` definition.

| Section | Change Type | Old Text Snippet | New Text Snippet |
| :--- | :--- | :--- | :--- |
| **1.1 Strategy Tags** (Exclusionary Note) | **Modified** | *Important note: If a turn consists of only a rhetorical filler, a neutral follow-up comment, or simply a backchanneling sound that does not add any meaningful content to the conversation, do not annotate that turn with any strategy tag. Leave the strategy_tags field empty.* | *Important note for exclusion: Do not annotate a turn if it consists only of short, non-emotional backchanneling sounds that act as simple placeholders (eg. "Uh huh", "Mhm", "Oh" not tied to surprise/emotion, or neutral, non-affirming instances of "Yeah" or "Okay"). **All greetings, clear acknowledgments, and statements that serve an explicitly defined strategic function (as defined in 1.1) MUST be annotated.*** |
| **1.1 Strategy Tags** (Exclusionary Examples) | **REMOVED** | *For example, do not tag turns like: "Uh huh" "Mhm" "Oh" "Yeah" or "Okay" (when used as a simple placeholder, rather than affirming or emotionally encouraging the child)* | **[This section was removed to eliminate redundancy.]** |
