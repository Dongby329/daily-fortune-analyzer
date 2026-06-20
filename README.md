# 🧧 今日运势分析器

> 星座 × 传统命理 × AI —— 输入出生信息，获得精准、有逻辑的每日运势报告。

[![Status](https://img.shields.io/badge/status-v2.0-brightgreen)]()
[![Lines](https://img.shields.io/badge/code-2613_lines-blue)]()
[![Commits](https://img.shields.io/badge/commits-54-blue)]()
[![Privacy](https://img.shields.io/badge/privacy-本地存储-green)]()

---

## ✨ 功能

### 🔮 运势分析
| 模块 | 说明 |
|------|------|
| 星座运势 | 12 星座判定 + 四维度（事业/感情/财运/健康） |
| 生肖运势 | 12 生肖 + 今日地支关系分析 |
| 八字排盘 | 年/月/日/时四柱 + 日主 + 十神（五虎遁/五鼠遁） |
| 综合评分 | 星座×八字加权融合 0-100 分 + 一句话总结 |
| 性格解析 | 星座性格 × 八字日主交叉分析 |
| 人际契合 | 每日动态宜近/宜远人群特质推荐 |
| 幸运物 | 幸运色 + 数字 + 方位 + 五行强弱 |

### 🌌 超时空对话
| 模块 | 说明 |
|------|------|
| LLM 动态匹配 | 大模型根据命理特征匹配6位历史人物（中外混合） |
| 角色扮演聊天 | 搭载人物灵魂提示词，AI 以第一人称对话 |
| 历史记录 | 对话保存/查询/回放，最多 20 条 |

### 👕 AI 今日穿搭
| 模块 | 说明 |
|------|------|
| LLM 联网搜索 | 根据幸运色×性别×季节生成 6 套时尚搭配 |
| 平台直达 | 每套附小红书/Pinterest/微博搜索链接 |
| 双页同步 | 穿搭页生成结果自动同步至运势页 |

### 🔐 账号系统
| 模块 | 说明 |
|------|------|
| 注册/登录 | 本地账号，分配 FT-XXXX 唯一 ID |
| 记住我 | 勾选后下次自动登录，跳过登录页 |
| 快速登录 | 退出后一键填入用户名，仅需密码 |
| 我的 | 头像自定义（上传/表情）、性别、生日编辑、LLM 配置 |

---

## 🚀 使用

```bash
# 浏览器直接打开
open index.html
```

1. 注册账号（用户名+密码）
2. 填写出生日期和时间
3. 查看今日运势
4. 配置 LLM → 解锁超时空对话和 AI 穿搭

> **隐私**：所有数据仅存储在浏览器本地 localStorage，不上传。

---

## 🏗 技术架构

```
index.html（单文件 / 2613 行 / 111 KB）
├── HTML   · Tailwind CSS CDN · 响应式（移动+桌面）
├── CSS    · 黑色主题 · 星空动效 · SplitText 入场 · 动效系统
├── JS     · 纯客户端计算 · 零后端 · 零数据库
├── 🔮 星座引擎    · 12星座日期判定 + 元素属性运算
├── ☯️ 八字引擎    · 五虎遁/五鼠遁/节气判定/万年历日柱
├── 🔀 融合引擎    · 加权评分（有/无出生时间双权重）
├── 🤖 LLM 集成    · OpenAI 兼容 API（支持 DeepSeek/通义/智谱...）
└── 🔒 隐私保护    · localStorage · 不上传个人信息
```

### LLM 服务商支持

| 服务商 | 模型 |
|--------|------|
| DeepSeek | deepseek-chat / v4-flash / v4-pro |
| OpenAI | gpt-4o / 4o-mini / 4-turbo / 3.5-turbo |
| 通义千问 | qwen-plus / qwen-max / qwen-turbo |
| 智谱 GLM | glm-4-flash / glm-4 / glm-4-plus |
| Moonshot | moonshot-v1-8k / 32k / 128k |

---

## 📁 项目结构

```
to-c-week1-daily-fortune-analyzer/
├── index.html                   ← 完整应用
├── README.md                    ← 本文件
├── docs/
│   ├── requirements.md          ← 需求分析报告
│   ├── competitive-research.md  ← 竞品分析（12 款）
│   ├── market-analysis.md       ← 市场分析（$12-50 亿赛道）
│   ├── prd.md                   ← PRD v2.0
│   └── flowcharts/
│       ├── user-journey.md      ← 用户旅程
│       ├── fortune-calculation.md ← 推算逻辑
│       └── system-architecture.md ← 系统架构
└── prototype/
    ├── index.html               ← 原型入口
    ├── input.html               ← 输入页原型
    └── result.html              ← 报告页原型
```

---

## 🎯 差异化

与市面同类产品的核心区别：

1. **星座×八字统一评分** — 竞品无人做到融合打分
2. **LLM 动态人物匹配** — 非静态库，每次联网生成
3. **AI 联网穿搭搜索** — 带平台直达链接
4. **全本地存储** — 隐私零泄露，无需信任任何服务器
5. **小而精** — 4 个 Tab 覆盖核心场景，不做功能堆砌

---

## 📊 项目统计

| 指标 | 数值 |
|------|------|
| 代码行数 | 2,613 |
| 文件大小 | 111 KB |
| JS 函数 | 102 个 |
| Git 提交 | 54 次 |
| 文档 | 7 份 |
| 原型 | 3 个 |
| 累计功能 | 15 个核心模块 |

---

## 📄 许可

仅供娱乐参考 · 传统文化科普 · 命运掌握在自己手中

*Built with ❤️ · Product Manager Weekly*
