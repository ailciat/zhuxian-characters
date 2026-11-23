# Zhu Xian · Lu Xueqi / Bi Yao — Character Distillation

Two fan-made, ready-to-use artifacts distilled from the full text of the Chinese xianxia novel *Zhu Xian* (诛仙, "Jade Dynasty"): an **Agent Skill** (thinking framework + speech style) and a **SillyTavern character card** (chara_card_v3 with data embedded in a PNG).

> Fan work for study and personal entertainment only. Non-commercial. *Zhu Xian*, its characters and related rights belong to its author Xiao Ding (萧鼎) and the rights holders. This repository contains no text from the original novel — every line here is a summary or a rewrite. All key art is AI-generated fan illustration, not official artwork.

## Contents

| Character | Skill | Card | One-liner |
|---|---|---|---|
| Lu Xueqi (陆雪琪) | [`skills/luxueqi-perspective`](skills/luxueqi-perspective) | [`cards/陆雪琪_chara_card.png`](cards/陆雪琪_chara_card.png) | Eldest disciple of Mount Little Bamboo in the Qingyun Sect; the frost-sword immortal whose rigid pride hides everything soft |
| Bi Yao (碧瑶) | [`skills/biyao-perspective`](skills/biyao-perspective) | [`cards/碧瑶_chara_card.png`](cards/碧瑶_chara_card.png) | Only daughter of the Ghost King; a girl in water-green with a bell at her waist — sharp tongue, reckless heart |

## Using the Skills

Each skill is a folder:

```
luxueqi-perspective/
├── SKILL.md                    # roleplay rules, core principles, language rules, resource index
├── soul.md                     # drives, values, emotional core
├── limit.md                    # boundaries: what not to write, what not to do
└── resource/
    ├── speech_patterns.md      # tone layers, sentence templates, banned words
    ├── behavior_guide.md       # situation-response table, small gestures
    ├── relationship_dynamics.md# relations with Shuiyue, Wenmin, Zhang Xiaofan, Bi Yao, etc.
    └── key_life_events.md      # timeline, turning points, memory anchors
```

Install by dropping the folder into your skills directory (e.g. `~/.claude/skills/`), then invoke:

```
/陆雪琪_chat How do you see Zhang Xiaofan?
/碧瑶_chat Why do you always call him an idiot?
```

The hard rule at the top of each SKILL.md: **always answer in the language of the question**, including when quoting the source.

## Using the Cards

- `cards/*_chara_card.png` — 1254×1881 portrait with both `chara` and `ccv3` `tEXt` chunks in the PNG. Drag it into SillyTavern → *Character Management → Import* and it loads the persona, first message and lorebook.
- `cards/*_chara_card.json` — same payload as plain JSON (chara_card_v3), for text-only consumers.
- Six lorebook entries per card:
  - Lu Xueqi: Tianya sword / Little Bamboo Peak & Master Shuiyue / Zhang Xiaofan / Bi Yao / Wangyue Terrace / the Abyss of Dead Spirits
  - Bi Yao: Shangxin Flower / Hehuan Bell / Ghost King sect & family / the Six-Fox Cave / Zhang Xiaofan / the Art of Infatuation

## How it was made

1. Split the 257 chapters (~1.6M characters) on chapter headings.
2. Count appearances: Lu Xueqi in 119 chapters, Bi Yao in 99.
3. Extract paragraph-level evidence from hit chapters (sentences naming the character plus nearby context), compress into evidence packs, then read them through.
4. Distill character core, tone layers, relationship dynamics, timeline and boundaries — then generate the skill and the card separately.

No external LLM API is involved; the model reads and writes everything directly.

## Design decisions

- Key art is original, AI-generated Chinese-style fan illustration, not official art.
- The Bi Yao card uses her living period (Mount Liubo to Mount Qingyun); it does not cover the ten-year slumber.
- The Lu Xueqi card opens on Wangyue Terrace; the conversation can move to the Abyss, the refused marriage, or the reunion ten years later.
- Daily details absent from the novel are inferred from character, never invented as explicit scenes.

## Acknowledgements

The output format and production pipeline follow [JodieRuth/GalgameCharacterSkills](https://github.com/JodieRuth/GalgameCharacterSkills), a Galgame character-distillation tool:

- The skill folder layout (`SKILL.md` / `soul.md` / `limit.md` / `resource/{speech_patterns,behavior_guide,relationship_dynamics,key_life_events}.md`) follows its spec.
- The cards use its chara_card_v3 format, and embed the card JSON as base64 in a PNG `tEXt` chunk the same way it does (this project also writes an extra `ccv3` chunk).
- The overall pipeline — slice, extract, archive per character, then generate skill and card — is modelled on that project.

The only difference is the generation side: the original tool requires your own LLM API, whereas this project has the model read the text and write everything directly, with no external API calls.

## Disclaimer

A fan project, unaffiliated with Xiao Ding, the rights holders of *Zhu Xian*, or any official body. Rights holders may request removal of any content.
