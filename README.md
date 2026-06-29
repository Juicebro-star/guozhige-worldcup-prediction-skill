# 果汁哥世界杯赛前判断与内容生产 Skill

复用"果汁哥世界杯分析"工作流的 Agent Skill。让模型在世界杯/足球内容输出时,遵守统一的分析口径、输出结构和安全边界。

## 核心能力

- 世界杯/足球**常规时间(90分钟)**胜平负判断;
- 单场深度分析、今日多场清晰预测、群内短回复;
- 净胜球倾向解释(不提供投注建议);
- 海报 / PDF 报告 / 腾讯问卷提示词;
- 赛后复盘;
- **果汁哥口吻**:兄弟感+直播感+梗感的语气库,让输出像果汁哥本人聊球,而不是 AI 助手;
- **先查最新数据再判断**:内置公开数据源清单与查询工作流,不靠模型记忆猜赛果。

## 目录结构

```
guozhige_worldcup_prediction_skill/
├── SKILL.md                  # 核心:口径、原则、安全边界、数据工作流、果汁哥语气、检查清单
└── references/
    ├── voice.md              # 果汁哥口头禅库 + 世界杯专用梗 + 强度分层与边界
    ├── data-sources.md       # 公开数据源 + "查什么/怎么用进判断"
    ├── templates.md          # 全部输出模板
    ├── expressions.md        # 常用表达句式库
    ├── reports.md            # PDF/海报/问卷详细要求
    └── examples.md           # 样例判断(纯占位符,仅示范结构与语气)
```

## 安装

**Claude Code / Agent SDK**:把整个文件夹放到 skills 目录下,模型会按需自动加载。

- 用户级:`~/.claude/skills/guozhige_worldcup_prediction_skill/`
- 项目级:`<项目>/.claude/skills/guozhige_worldcup_prediction_skill/`

放好后,当用户提出"预测今晚比赛胜平负""做一份世界杯分析报告/海报/问卷""赛后复盘"等需求时,skill 会被触发。`SKILL.md` 的 frontmatter `description` 决定触发时机。

其他平台:把 `SKILL.md`(及 `references/`)放入对应的 Skill / 知识库即可。

## 设计说明

数据工作流借鉴了 [machina-sports/sports-skills](https://github.com/machina-sports/sports-skills)(标准 SKILL.md 格式、接 ESPN/Understat/Transfermarkt 等公开源)和 [withqwerty/nutmeg](https://github.com/withqwerty/nutmeg)(查真实文档而非训练记忆)。本 skill 的独特价值是"果汁哥的判断框架 + 可发群的内容生产链路";具体赛前事实必须实时获取。
