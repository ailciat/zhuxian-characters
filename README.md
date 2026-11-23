# 诛仙 · 陆雪琪 / 碧瑶 角色蒸馏

![封面](preview/cover.png)

**中文** | [English](README.en.md)

许可协议：[MIT](LICENSE) · 同人二创，非官方

把《诛仙》全本里三个角色的言行蒸馏成两种可直接用的产物：**Agent Skill**（思维框架 + 表达方式）和 **SillyTavern 角色卡**（chara_card_v3，PNG 内嵌）。

> 同人二创，非官方，仅供学习与个人娱乐。《诛仙》原著及角色版权归作者萧鼎及相关版权方所有；本仓库不包含原著正文，所有文本均为基于原文的归纳与二次撰写，立绘为 AI 生成的原创同人图。

## 目录

| 角色 | Skill | 角色卡 | 一句话人设 |
|---|---|---|---|
| 陆雪琪 | [`skills/luxueqi-perspective`](skills/luxueqi-perspective) | [`cards/陆雪琪_chara_card.png`](cards/陆雪琪_chara_card.png) | 青云门小竹峰水月大师嫡传，持天琊的冰霜剑仙，冷壳底下宁折不弯 |
| 碧瑶 | [`skills/biyao-perspective`](skills/biyao-perspective) | [`cards/碧瑶_chara_card.png`](cards/碧瑶_chara_card.png) | 鬼王宗宗主独女，水绿衣裳一铃音，嘴硬心软的烈性少女 |
| 张小凡 | [`skills/zhangxiaofan-perspective`](skills/zhangxiaofan-perspective) | [`cards/张小凡_chara_card.png`](cards/张小凡_chara_card.png) | 大竹峰第七弟子，憨直倔强的凡人少年；十年后成了鬼王宗的血公子鬼厉 |

## Skill 用法

每个 Skill 是一个目录：

```
luxueqi-perspective/
├── SKILL.md                    # 扮演规则 + 核心原则 + 语言规则 + 资源索引
├── soul.md                     # 内在驱动、价值观、情感内核
├── limit.md                    # 边界：不写什么、不做什么
└── resource/
    ├── speech_patterns.md      # 语气分层、句式模板、禁用词
    ├── behavior_guide.md       # 情境反应表、小动作库
    ├── relationship_dynamics.md# 与水月、文敏、张小凡、碧瑶等人的关系
    └── key_life_events.md      # 时间线、转折、记忆锚点
```

安装：把目录放进你的 skills 目录（Claude Code 为 `~/.claude/skills/`，其他 Agent 放到对应 skill root），激活：

```
/陆雪琪_chat 你怎么看张小凡
/碧瑶_chat 你为什么总叫他呆子
/张小凡_chat 师父又骂你了，你怕不怕
```

SKILL.md 顶部写着硬规则：**全程使用与提问相同的语言**，引用原文也必须翻译。

## 角色卡用法

- `cards/*_chara_card.png`：1254×1881 立绘，PNG 的 `tEXt` 里同时写了 `chara` 与 `ccv3` 两段数据。SillyTavern 拖进「角色管理 → 导入」即可读出设定、开场白与世界书。
- `cards/*_chara_card.json`：同内容的纯 JSON（chara_card_v3），用于需要文本的场合。
- 每张卡附 6 条世界书条目：
  - 陆雪琪：天琊神剑 / 小竹峰与水月 / 与张小凡 / 碧瑶 / 望月台 / 死灵渊
  - 碧瑶：伤心花 / 合欢铃 / 鬼王宗与家人 / 六狐洞往事 / 与张小凡 / 痴情咒
  - 张小凡：烧火棍与噬血珠 / 大竹峰与师父师娘 / 田灵儿 / 碧瑶 / 陆雪琪 / 鬼厉

## 做法

按章节定位三人的出场段落，抽取对白与关键叙述后通读归纳，再分别生成 Skill 与角色卡。全程由模型直接阅读文本完成，不依赖任何外部 LLM API。

## 设定取舍

- 立绘为 AI 原创生成的国风同人插画，非官方美术。
- 碧瑶卡默认取其在世时点（流波山—青云山之间），不含十年沉睡后的状态。
- 陆雪琪卡默认情境为望月台，可随对话推进到死灵渊、拒婚、十年后等阶段。
- 原文未明确写出的日常细节按人物性格推断，不编写露骨情节。

## 致谢

本项目的产物规范与制作流程，来自 [JodieRuth/GalgameCharacterSkills](https://github.com/JodieRuth/GalgameCharacterSkills)（Galgame 角色蒸馏工具）：

- Skill 文件夹结构（`SKILL.md` / `soul.md` / `limit.md` / `resource/{speech_patterns,behavior_guide,relationship_dynamics,key_life_events}.md`）沿用其定义的标准；
- 角色卡采用其规定的 chara_card_v3 格式，并按它的做法把卡片 JSON 以 base64 写入 PNG 的 `tEXt` 块（本项目额外多写一份 `ccv3`）；
- 「分段抽取 → 角色归档 → 生成 Skill / 角色卡」的整体流水线同样参照该项目。

区别只在于生成端：原工具需要自备 LLM API，本项目由模型直接阅读文本完成归纳，全程未调用外部 API。

## 免责声明

1. **非官方**：本项目为粉丝自制同人二创，与萧鼎、《诛仙》原著版权方及任何官方机构、平台均无关联，未获其授权或认可。
2. **版权归属**：《诛仙》原著小说、角色名称、世界观及相关设定的著作权归作者萧鼎及相关版权方所有。本仓库不包含原著正文，全部内容为基于原文的归纳、改写与二次创作。
3. **授权范围**：本仓库原创内容（Skill 文本、角色卡、文档）以 MIT 协议授权，可自由使用、修改与再分发。但 MIT 不授予《诛仙》原著、角色名称与相关设定的任何权利；若将本项目用于商业用途，仍可能构成对原著权利的侵犯，须自行取得权利人许可。
4. **AI 生成标注**：立绘为 AI 生成的原创同人插画；角色设定、Skill 与角色卡文本由模型阅读原著后撰写，可能存在偏差或遗漏，不代表官方设定。
5. **不保证准确**：内容为二次创作，可能与原著细节、他人理解或后续官方衍生作品存在差异，不作为考据依据。
6. **风险自负**：使用者自行承担使用本项目（含在对话平台、角色卡宿主软件中加载）产生的一切后果，作者不对任何直接或间接损失负责。
7. **平台与法律**：使用者须遵守所在平台的内容规范与当地法律法规，不得将本项目内容用于违法违规用途。
8. **通知即删**：若权利人认为本项目内容侵犯其合法权益，请通过仓库 Issue 联系，作者将在核实后立即删除或修改相关内容。
9. **无担保**：本仓库按「现状」提供，不附带任何明示或暗示的担保。

## 许可协议

本仓库原创内容采用 MIT 协议，全文见 [LICENSE](LICENSE)。该协议仅覆盖作者原创内容，不涉及《诛仙》原著权利。
