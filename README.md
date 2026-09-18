# English Word Video Teaching

Claude Code slash command for English vocabulary teaching and MiniMax H3 video prompt generation.

## Usage

Install the command globally:

    mkdir -p ~/.claude/commands
    git clone https://github.com/TheSongg/english-word-video-skill.git /tmp/english-word-video-skill
    cp /tmp/english-word-video-skill/commands/english-word.md ~/.claude/commands/english-word.md

Restart Claude Code after installation.

Then use:

    /english-word atmosphere

Or:

    /english-word atmosphere，生成 MiniMax H3 教学视频提示词

## What it does

1. Analyzes the common meanings of the word.
2. Gives one natural English example sentence for each meaning.
3. Explains the usage context and semantic cues.
4. Generates a MiniMax H3 Full-Reference prompt when image/audio references are available.

## MiniMax H3 prompt structure

The video prompt contains these six sections in this exact order:

1. subject_definitions
2. summary
3. retention_analysis
4. detailed_description
5. overall_soundscape
6. non_diegetic_music

For one character image plus one voice reference, the default task type is:

    [reference generation + audio reference]

The audio is treated as a voice reference unless the user explicitly requests audio reuse.

## Repository structure

    english-word-video-skill/
    ├── README.md
    ├── SKILL.md
    └── commands/
        └── english-word.md

## Update

To update the command:

    cd /tmp/english-word-video-skill
    git pull
    cp commands/english-word.md ~/.claude/commands/english-word.md

## MiniMax H3 reference

Official guide:

https://huggingface.co/MiniMaxAI/MiniMax-H3/blob/main/docs/VIDEO_PROMPT_WRITING_GUIDE_ref_en.md