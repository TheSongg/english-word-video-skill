---
description: Analyze an English word, explain common meanings and contexts, and generate a MiniMax H3 teaching-video prompt
---

# English Word Video Teaching

用户输入：
$ARGUMENTS

根据用户提供的英语单词执行以下任务。

## 1. 单词分析
给出：单词、音标、常用词性、主要常用含义。只保留实际常用的主要含义，不要罗列罕见词义。

## 2. 含义、语境与例句
对于每一个主要含义，给出：词性、中文含义、使用语境、语境说明、英文例句。每个含义默认只给一个例句。
语境说明必须解释这个含义通常在什么场景使用、语体或领域，以及帮助学习者判断该含义的语义线索。
例句必须自然、准确，并与该含义严格对应。如果用户提供指定例句，应优先保留。

## 3. MiniMax H3 视频提示词
如果用户提供人物参考图和参考音频，生成完整的 MiniMax H3 Full-Reference Prompt。
必须严格按照以下六个 section 输出，顺序不能改变：
1. subject_definitions
2. summary
3. retention_analysis
4. detailed_description
5. overall_soundscape
6. non_diegetic_music

### Reference 规则
对于一个人物参考图 + 一个参考音频：
- <Subject 1>：人物参考
- <Picture 1>：当图片承担具体画面、构图或关键帧锚点作用时使用；如果图片仅用于人物身份/外观参考，则不要额外建立 standalone <Picture 1>
- <Audio 1>：声音参考
- (S1)：说话人物
声音参考应定义为：<Audio 1> is the voice-timbre reference for <Subject 1> (S1).
默认任务类型：[reference generation + audio reference]。
除非用户明确要求复制源音频，否则不要使用 audio reuse。
不要因为存在人物图片就自动使用 keyframe completion。

### retention_analysis
人物视觉参考通常使用：<Subject 1>: fully_preserved。
参考音频通常使用：<Audio 1>: reference。
明确说明人物身份和外观保持一致；音频只用于参考音色、语速、节奏、表达方式等，不复制源音频信号。
不要虚构人物参考图或参考音频中没有确认的信息。

## 4. detailed_description
这是主要的视频生成内容，使用英文。
开头先使用 1–2 个英文句子描述整体视觉风格，然后使用 [Shot 1] ...、[Shot 2] At 00:SS.mmm, ... 按播放顺序描述镜头。
默认约 350–500 个英文单词，除非用户要求更短。
必须描述人物动作、表情、手势、说话方式、环境、灯光、景别、摄像机运动、镜头衔接和对白。
人物对白使用：(S1) <d>[English] ...</d>。
目标单词应该在对白中自然强调。
视频应该让画面帮助学习者理解目标词义，而不是单纯让人物面对镜头念句子。

## 5. 默认视频风格
用户没有特别要求时：realistic educational video；natural presenter behavior；clean and uncluttered indoor environment；soft believable lighting；medium shot or medium close-up；natural eye contact；friendly and focused teaching expression；moderate speaking pace；clear English pronunciation；small controlled hand gestures；subtle head movement；stable camera；restrained camera movement。
避免 exaggerated gestures、cartoonish acting、rapid camera movement、unnecessary zooms、excessive scene changes、artificial facial expressions、distracting props、large blocks of on-screen text、unrequested subtitles、unnecessary music。

## 6. Sound
### overall_soundscape
只描述 diegetic / physical sound，例如安静室内或教室环境声、细微环境声、自然动作声和清晰对白。环境声音不能压过人物对白。
### non_diegetic_music
默认 N/A。只有用户明确要求音乐，或者创意要求确实需要音乐时才加入。

## 7. 最终检查
检查六个 section 全部存在且顺序正确；所有 reference 有定义；<Subject 1> 与人物参考图关系正确；<Audio 1> 正确关联 (S1)；task type 正确；没有错误使用 audio reuse 或 keyframe completion；对白使用 (S1) 和 <d>[English] ...</d>；例句和目标含义一致；视觉场景帮助理解词义；没有虚构参考资产信息。

## 8. 最终输出格式
按照：1. 单词概览；2. 常用含义；3. 例句与语境；4. MiniMax H3 视频提示词。
如果需要为多个词义分别制作视频，则每个词义分别生成一套完整的六 section Prompt。

## Official Reference
https://huggingface.co/MiniMaxAI/MiniMax-H3/blob/main/docs/VIDEO_PROMPT_WRITING_GUIDE_ref_en.md