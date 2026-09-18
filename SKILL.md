---
name: english-word-video-teaching
description: >
  根据用户提供的英语单词，整理常用词义、例句和适用语境，并生成基于人物参考图和参考音频的 MiniMax H3 英语单词教学视频提示词。
---

# English Word Video Teaching

## Goal
For an English word, provide:
1. Common practical meanings.
2. One natural example sentence for each meaning.
3. Context and usage explanation for each meaning.
4. A complete MiniMax H3 full-reference video prompt when a character image and reference audio are supplied.

## Meaning analysis
For each major common sense:
- Give the part of speech when useful.
- Explain the meaning in concise Chinese.
- Explain when/where/how this sense is normally used.
- Identify register or domain when relevant.
- Give exactly one natural example sentence unless more are requested.
- Do not over-fragment trivial grammatical variations or include obscure senses without a reason.

The context explanation must describe the actual usage situation and semantic cues, not merely provide a synonym.

If the user supplies an example sentence, preserve it unless correction or rewriting is requested.

## Video mode
For one character image plus one reference audio:
- Treat the image primarily as a visual/character reference.
- Treat the audio as a voice reference unless the user explicitly requests audio reuse.
- Default task type: [reference generation + audio reference].
- Do not use audio reuse unless the source audio itself must be copied.
- Do not use keyframe completion merely because an image exists; use it only when the image is intended as the target keyframe/composition to be completed.

Do not invent visual or audio properties that cannot be inspected or that the user did not specify.

## Reference definitions
Use MiniMax H3 full-reference terminology:
- <Picture 1>: supplied image when it is a concrete frame/composition anchor.
- <Subject 1>: the character represented by the image.
- <Audio 1>: supplied audio reference.
- (S1): speaking character.

If the image only defines character identity/appearance and is not a target-frame composition anchor, cite it inside <Subject 1> rather than creating an unnecessary standalone picture definition.

When audio guides the speaker's voice:
<Audio 1> is the voice-timbre reference for <Subject 1> (S1).

Use reference labels when the referenced asset first appears and wherever its role is relevant.

## Retention semantics
Typical visual reference:
<Subject 1>: fully_preserved — preserve character identity and visual appearance.

Typical voice reference:
<Audio 1>: reference — use timbre, speaking rhythm, delivery, and relevant vocal characteristics without copying the source audio signal.

## Required prompt structure
The final MiniMax H3 full-reference prompt MUST contain these six sections in this exact order:
1. subject_definitions
2. summary
3. retention_analysis
4. detailed_description
5. overall_soundscape
6. non_diegetic_music

Do not rename, reorder, or omit sections.

### subject_definitions
Define every reference used. Do not invent age, clothing, hairstyle, environment, facial features, or voice properties.

### summary
State:
- task type;
- teaching scenario;
- target word meaning;
- spoken example sentence;
- key visual idea.

For the standard image + voice-reference case use:
[reference generation + audio reference]

### retention_analysis
State what is preserved and how each reference is used. Distinguish fully_preserved from reference semantics.

### detailed_description
This is the main shot-by-shot description. For generation tasks, normally write about 350–500 English words unless the user requests a shorter prompt.

Start with 1–2 English sentences describing the overall visual style, then use:
[Shot 1] ...
[Shot 2] At 00:SS.mmm, ...

Include:
- character behavior and expressions;
- body movement;
- environment and lighting;
- camera framing and restrained movement;
- dialogue;
- reference labels;
- playback order.

Dialogue format:
(S1) <d>[English] The dialogue goes here.</d>

For vocabulary teaching, the target example sentence should normally be spoken naturally by (S1), with a slight natural emphasis on the target word.

### overall_soundscape
Describe diegetic physical sound only, such as quiet room/classroom ambience and subtle movement sounds. Keep it subordinate to dialogue.

### non_diegetic_music
Use N/A by default. Add music only when explicitly requested or clearly required by the creative brief.

## Teaching-video defaults
Unless overridden:
- realistic educational video;
- natural presenter behavior;
- clean uncluttered indoor environment;
- soft believable lighting;
- medium shot or medium close-up;
- natural eye contact;
- friendly focused teaching expression;
- moderate speaking pace;
- clear English pronunciation;
- small controlled hand gestures;
- subtle head movement;
- stable camera with restrained movement.

Avoid by default:
- exaggerated gestures;
- cartoonish acting;
- rapid camera movement;
- unmotivated zooms;
- excessive scene changes;
- artificial facial expressions;
- distracting props;
- large blocks of on-screen text;
- unrequested subtitles or graphics.

## Make the meaning visual
Concrete meanings should be reinforced by relevant objects, actions, places, or events when useful.
Abstract meanings should use appropriate social, emotional, environmental, or situational cues.
The visual situation and example sentence must represent the same sense.

## Workflow
1. Identify major common senses.
2. Write one example sentence per sense.
3. Explain context and semantic cues.
4. Build a coherent teaching scenario.
5. Generate the six-section MiniMax H3 prompt.
6. Validate the result.

Validation checklist:
- all six sections exist and are ordered correctly;
- every referenced asset is defined;
- <Subject 1> is tied to the character image when applicable;
- <Audio 1> is tied to (S1) when used as voice reference;
- task type matches reference usage;
- audio reuse is not used accidentally;
- dialogue uses (S1) and <d>[English] ...</d>;
- example sentence matches the selected sense;
- visuals reinforce the selected sense;
- no unsupported asset details are invented.

## User-facing output
Return in this order:
1. 单词概览
2. 常用含义
3. 例句与语境
4. MiniMax H3 视频提示词

If multiple meanings need videos, create a separate complete six-section prompt for each meaning.

## Official reference
https://huggingface.co/MiniMaxAI/MiniMax-H3/blob/main/docs/VIDEO_PROMPT_WRITING_GUIDE_ref_en.md
