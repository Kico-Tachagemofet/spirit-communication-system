# Spirit Communication System v5.0

> 灵体沟通辅助系统 — 基于塔罗牌阵、字卡、占星骰子、易经和筊杯的结构化占卜协议。

## 关于

此项目包含 Spirit Communication System 的完整规则文档和配套 Python 脚本。AI 执行完整的符号抽取 → 解读 → 筊杯验证闭环。

配合 [SpiritTool](https://github.com/Kico-Tachagemofet/Project-Hermes) 桌面应用使用，或直接调用脚本进行命令行占卜。

## 项目结构

```
spirit-communication-system/
├── spirit-communication-system.md   # 系统规则文档
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

Python 3.10+，**仅使用标准库**，无需 pip install 任何第三方包。

## 快速开始

```bash
# 塔罗 + 占星骰子
python3 scripts/spirit_draw_v2.py

# 易经起卦
python3 scripts/yijing_draw.py

# Hermes 字卡
python3 scripts/wordcard_hermes.py

# 筊杯（掷1次）
python3 scripts/jiaobei.py

# 筊杯（批量5次）
python3 scripts/jiaobei.py 5

# 雷诺曼（3张）
python3 scripts/lenormand.py
```

## 符号系统

| 符号系统 | 脚本 | 说明 |
|---------|------|------|
| 塔罗牌阵 | `spirit_draw_v2.py` | 92张卡池（78标准 + 14奇迹），6位牌阵 |
| 占星骰子 | 含于 `spirit_draw_v2.py` | 行星 × 星座 × 宫位 + 尊贵状态 + 飞星 |
| 易经 | `yijing_draw.py` | 64卦，含本卦、变爻、之卦 |
| 字卡 | `wordcard_hermes.py` | Hermes 字卡词库，随机抽3张 |
| 筊杯 | `jiaobei.py` | 圣杯（确认）/ 笑杯（保留）/ 阴杯（偏差） |
| 雷诺曼 | `lenormand.py` | 36张雷诺曼牌 |

## 解读流程

1. 确认沟通对象和问题
2. 执行脚本抽取符号
3. 符号学解读（先发散，再收束）
4. 筊杯验证 → 笑杯自主细化 / 阴杯偏差定位
5. 输出最终解读

详见 [spirit-communication-system.md](spirit-communication-system.md)。

## License

MIT
