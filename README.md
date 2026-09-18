# English Word Video Teaching Skill

An AI skill for turning an English word into a vocabulary-teaching package and a MiniMax H3 video-generation prompt.

## Features
- Common word meanings with concise Chinese explanations.
- One natural example sentence per meaning.
- Usage context and semantic cues.
- Visual teaching scenario.
- MiniMax H3 full-reference prompt for one character image plus one voice reference.
- Exact six-section full-reference structure.

## Workflow
Input may include an English word, target meaning, example sentence, video requirements, character/image reference, and voice/audio reference.

Output:
1. Word overview
2. Common meanings
3. Example sentence and context for each meaning
4. Complete MiniMax H3 prompt

## MiniMax H3 reference
Official guide:
https://huggingface.co/MiniMaxAI/MiniMax-H3/blob/main/docs/VIDEO_PROMPT_WRITING_GUIDE_ref_en.md

Required sections:
1. subject_definitions
2. summary
3. retention_analysis
4. detailed_description
5. overall_soundscape
6. non_diegetic_music

For a character image plus voice reference, the default task type is:
[reference generation + audio reference]

The audio is treated as a voice reference unless the user explicitly requests audio reuse.
