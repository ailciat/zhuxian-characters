# Zhu Xian · Lu Xueqi / Bi Yao — Character Distillation

Two fan-made, ready-to-use artifacts distilled from the full text of the Chinese xianxia novel *Zhu Xian* (诛仙, "Jade Dynasty"): an **Agent Skill** (thinking framework + speech style) and a **SillyTavern character card** (chara_card_v3 with data embedded in a PNG).

[中文](README.md) | **English**

License: [MIT](LICENSE) · fan-made, unofficial

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

## Approach

Locate each character's scenes chapter by chapter, extract the dialogue and key narration, read it through, then generate the skill and the card separately. Everything is read and written directly by the model — no external LLM API is involved.

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

1. **Unofficial.** This is a fan-made derivative work. It is not affiliated with, authorised by, or endorsed by Xiao Ding, the rights holders of *Zhu Xian*, or any official body or platform.
2. **Ownership.** Copyright in the novel *Zhu Xian*, its characters, names and world-building belongs to its author Xiao Ding and the rights holders. This repository contains no text from the original novel; all content is summary, rewrite or secondary creation.
3. **Scope of grant.** Original content in this repository (skill text, character cards, documentation) is licensed under MIT and may be used, modified and redistributed freely. MIT grants no rights in the novel *Zhu Xian*, its characters or world-building; commercial use of that IP may still infringe the rights holders and requires their permission.
4. **AI-generated.** Key art is AI-generated original fan illustration. The persona text, skills and cards were written by a model after reading the novel and may contain errors or omissions; they do not represent official canon.
5. **No guarantee of accuracy.** The content is derivative and may differ from the original text, from other readers' interpretations, or from later official works. It is not a reference for canon research.
6. **Use at your own risk.** Users bear all consequences of using this project, including loading it in chat platforms or character-card host software. The author is not liable for any direct or indirect loss.
7. **Platform rules and law.** Users must comply with the content policies of their platform and with local laws, and must not use this content for unlawful purposes.
8. **Notice and takedown.** If a rights holder believes this content infringes their rights, please open an Issue; the author will remove or amend the relevant content promptly after verification.
9. **No warranty.** Provided "as is", without any express or implied warranty.

## License

Original content in this repository is licensed under MIT, see [LICENSE](LICENSE). The license covers the author's original content only, not any rights in the original novel.
