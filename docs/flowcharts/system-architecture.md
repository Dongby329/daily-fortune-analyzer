# 🏗 系统模块关系图 — 今日运势分析器 v2.0

> 单页应用，纯客户端计算，零后端服务器

---

## 第一层：用户交互流

```mermaid
sequenceDiagram
    participant U as 👤 用户
    participant UI as 🖥 前端界面
    participant Auth as 🔐 账号引擎
    participant Engine as ⚙️ 计算引擎
    participant LLM as 🤖 LLM API
    participant Data as 💾 localStorage

    U->>UI: 打开页面
    UI->>Auth: 检查登录态
    Auth->>Data: 读取 fortune_current
    Data-->>Auth: 已记住→自动登录

    U->>UI: 填写出生信息
    U->>UI: 点击「查看运势」
    UI->>Engine: 传入 {birthday, birthtime}
    Engine->>Engine: 星座+八字+生肖+融合
    Engine-->>UI: 运势报告
    UI->>Data: 保存出生信息

    U->>UI: 点击「超时空对话」
    UI->>Engine: 获取命理特征
    Engine->>LLM: 发送匹配请求
    LLM-->>UI: 6位人物
    U->>UI: 选择人物聊天
    UI->>LLM: 系统提示词+用户消息
    LLM-->>UI: 角色扮演回复
    UI->>Data: 保存对话记录

    U->>UI: 点击「穿搭」
    UI->>LLM: AI搜索搭配
    LLM-->>UI: 6套搭配+搜索链接
```

## 第二层：模块架构

```mermaid
flowchart TD
    subgraph 界面层
        A[📱 底部导航]
        B1[🔐 登录/注册页]
        B2[🔮 运势页\n输入+结果]
        B3[👕 穿搭页\nAI搜索+链接]
        B4[🌌 超时空对话页\n匹配+聊天]
        B5[👤 我的页\n信息+LLM配置+历史]
    end

    subgraph 引擎层
        C1[🔐 账号引擎\n注册/登录/记住/ID]
        C2[♈ 星座引擎\n12星座+星象]
        C3[☯️ 八字引擎\n四柱+日主+十神]
        C4[🐉 生肖引擎\n生肖+运程]
        C5[🔀 融合引擎\n加权评分]
        C6[📝 内容引擎\n性格/人际/幸运/文案]
        C7[🤖 LLM 桥接\nOpenAI兼容API]
    end

    subgraph 数据层
        D1[(fortune_users\n用户账号+配置)]
        D2[(fortune_current\n当前会话)]
        D3[(fortune_remembered\n记住列表)]
        D4[(fortune_chat_history\n对话记录)]
    end

    A --> B1 & B2 & B3 & B4 & B5
    B1 --> C1
    B2 --> C2 & C3 & C4 & C5 & C6
    B3 --> C2 & C3 & C7
    B4 --> C2 & C3 & C7
    B5 --> C1

    C1 --> D1 & D2 & D3
    B4 --> D4
```

## 第三层：数据存储结构

```mermaid
flowchart LR
    subgraph localStorage
        U[(fortune_users)]
        C[(fortune_current)]
        R[(fortune_remembered)]
        H[(fortune_chat_history)]
        V[(fortune_data_version)]
    end

    U --> |"userKey"| U1[username / password / id]
    U --> |"userKey"| U2[birthday / birthtime / gender]
    U --> |"userKey"| U3[avatar / llmEndpoint / llmKey / llmModel]
    C --> |"session"| C1[key / username / id / remember]
    R --> |"list"| R1[username1 / username2 / ...]
    H --> |"list"| H1[id / figureName / messages / date]
```

## 技术栈

| 层 | 技术 | 说明 |
|----|------|------|
| 界面 | HTML + Tailwind CSS CDN | 黑底极简，响应式移动+桌面 |
| 动效 | CSS @keyframes + JS SplitText | 逐字入场/淡入/缩放/滑入 |
| 星座 | 纯 JS 算法 | 12星座日期判定+元素属性 |
| 八字 | 纯 JS 算法 | 五虎遁/五鼠遁/节气/万年历 |
| 融合 | 加权评分 | 有/无出生时间双权重 |
| LLM | fetch API | OpenAI 兼容，支持5家服务商 |
| 存储 | localStorage | 4组key，带版本号+容量保护 |
| 隐私 | 纯本地 | 无服务器/无数据库/无追踪 |

## 技术边界

```
✅ 纯 HTML/CSS/JS 单页应用
✅ Tailwind CSS CDN
✅ 客户端计算，零后端
✅ 5家 LLM 服务商预设
✅ 本地账号系统（localStorage）
❌ 无服务器 / API / 数据库
❌ 无第三方追踪 / 分析
❌ 敏感数据不上传
```

---

*系统架构图 v2.0 · 含LLM集成 + 账号系统*
