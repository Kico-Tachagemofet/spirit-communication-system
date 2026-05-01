# Spirit Communication System v5.0

> 灵体沟通辅助系统 — Claude Code Agent / Hermes Skill

## 这是什么

这是给 **AI Agent 使用的系统配置**（skill / agent prompt），不是独立应用程序。

可以直接作为：
- **Claude Code** 的 agent 配置（放入 `.claude/agents/` 目录）
- **Hermes** 的 skill（放入 `~/.hermes/skills/` 目录）
- 其他兼容 OpenAI tool-calling 的 AI 工具的 system prompt

加载后，AI 会按照文档定义的规则执行完整的符号抽取 → 解读 → 筊杯验证闭环。

## 配套工具

本系统的脚本可以配合 [SpiritTool](https://github.com/Kico-Tachagemofet/Project-Hermes) 桌面应用使用，也可以直接命令行调用。

## 使用方式

### 作为 Claude Code Agent

将 `spirit-communication-system.md` 放入项目的 `.claude/agents/` 目录：

```yaml
# .claude/agents/spirit-communication-system.md
---
name: spirit-communication-system
description: "Spirit communication via tarot, I Ching, jiaobei verification"
model: opus
---
# ... 文档其余内容
```

### 作为 Hermes Skill

```bash
# 放入 Hermes skills 目录
cp spirit-communication-system.md ~/.hermes/skills/divination/
```

调用方式：在聊天中提及灵体沟通需求，Hermes 会自动加载此 skill。

### 脚本使用

文档中引用的脚本位于 `scripts/` 目录，所有脚本仅使用 Python 标准库。

```bash
# 塔罗 + 占星骰子
python3 scripts/spirit_draw_v2.py

# 易经起卦
python3 scripts/yijing_draw.py

# Hermes 字卡
python3 scripts/wordcard_hermes.py

# 筊杯验证
python3 scripts/jiaobei.py
```

## 项目结构

```
spirit-communication-system/
├── spirit-communication-system.md   # Agent / Skill 系统规则文档
├── scripts/
│   ├── spirit_draw_v2.py            # 92张塔罗牌阵 + 占星骰子
│   ├── yijing_draw.py               # 易经起卦（本卦/变爻/之卦）
│   ├── jiaobei.py                   # 筊杯验证
│   ├── lenormand.py                 # 雷诺曼牌
│   ├── tarot_astro_draw.py          # 简化3牌 + 占星骰子
│   ├── wordcard_hermes.py           # Hermes 字卡抽取
│   └── jiaobei_gua.py              # 茭杯起卦
└── data/
    └── 字卡-Hermes.md               # Hermes 字卡词库
```

## 依赖

Python 3.10+，**仅使用标准库**，无需 pip install。

## 符号系统

| 符号系统 | 脚本 | 说明 |
|---------|------|------|
| 塔罗牌阵 | `spirit_draw_v2.py` | 92张卡池（78标准 + 14奇迹），6位牌阵 |
| 占星骰子 | 含于 `spirit_draw_v2.py` | 行星 × 星座 × 宫位 + 尊贵状态 + 飞星 |
| 易经 | `yijing_draw.py` | 64卦，含本卦、变爻、之卦 |
| 字卡 | `wordcard_hermes.py` | Hermes 字卡词库，随机抽3张 |
| 筊杯 | `jiaobei.py` | 圣杯/笑杯/阴杯 |
| 雷诺曼 | `lenormand.py` | 36张牌 |

## License

MIT
