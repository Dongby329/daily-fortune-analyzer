# 🏗 系统模块关系图 — 今日运势分析器

> 前端单页应用，纯客户端计算，无需后端服务器

---

## 第一层：前端与用户交互流

```mermaid
sequenceDiagram
    participant U as 👤 用户
    participant UI as 🖥 前端界面
    participant Engine as ⚙️ 计算引擎
    participant Data as 📦 数据层

    U->>UI: 打开页面
    UI->>UI: 渲染表单 + 样式
    U->>UI: 填写出生日期 + 时间
    U->>UI: 点击「查看今日运势」

    UI->>Engine: 传入 {birthday, birthtime}
    Engine->>Data: 查询星座对照表
    Data-->>Engine: 返回星座类型
    Engine->>Data: 查询今日星象数据
    Data-->>Engine: 返回星象位置
    Engine->>Engine: 计算星座运势分

    Engine->>Data: 查询生肖对照表
    Data-->>Engine: 返回生肖类型

    alt 有出生时间
        Engine->>Engine: 排四柱八字 + 十神分析
        Engine->>Engine: 计算八字运势分
    else 无出生时间
        Engine->>Engine: 跳过八字，仅生肖
    end

    Engine->>Engine: 融合评分 + 性格解析 + 人际契合
    Engine-->>UI: 返回完整运势报告
    UI->>UI: 渲染报告（逐屏展示）
    UI-->>U: 展示综合评分 + 详细报告

    opt 用户点击分享
        U->>UI: 点击分享
        UI->>UI: 生成运势卡片图
        UI-->>U: 展示分享选项
    end
```

---

## 第二层：模块架构图

```mermaid
flowchart TD
    subgraph 前端界面层
        A[📱 首页表单\n出生日期+时间输入]
        B[📊 结果展示页\n综合评分+分类运势]
        C[📤 分享模块\n运势卡片生成]
    end

    subgraph 计算引擎层
        D[♈ 星座引擎\n星座判定+星象计算]
        E[☯️ 八字引擎\n四柱排盘+十神分析]
        F[🐉 生肖引擎\n生肖判定+运程计算]
        G[🔀 融合引擎\n加权评分+交叉分析]
    end

    subgraph 数据层
        H[🗓 星座对照表\n12星座日期范围]
        I[🌟 星象数据\n日月行星位置]
        J[📖 八字排盘表\n万年历+干支映射]
        K[🐲 生肖对照表\n年份→生肖]
        L[📝 文案模板库\n运势描述+性格文案]
    end

    A --> D
    A --> E
    A --> F
    D --> G
    E --> G
    F --> G
    D --> H
    D --> I
    E --> J
    F --> K
    G --> L
    G --> B
    B --> C
```

---

## 第三层：数据依赖关系

```mermaid
flowchart LR
    subgraph 输入
        I1[出生年]
        I2[出生月]
        I3[出生日]
        I4[出生时]
    end

    subgraph 静态数据
        S1[(星座日期表)]
        S2[(生肖对照表)]
        S3[(万年历干支表)]
        S4[(文案模板库)]
    end

    subgraph 动态数据
        D1[(今日星象位置)]
        D2[(今日日柱干支)]
    end

    subgraph 计算输出
        O1[星座类型]
        O2[生肖类型]
        O3[四柱八字]
        O4[星座运势分]
        O5[八字运势分]
        O6[生肖运势分]
        O7[综合评分]
        O8[性格画像]
        O9[人际契合]
        O10[幸运物推荐]
    end

    I2 & I3 --> S1 --> O1
    I1 --> S2 --> O2
    I1 & I2 & I3 & I4 --> S3 --> O3
    O1 & D1 --> O4
    O3 & D2 --> O5
    O2 & D2 --> O6
    O4 & O5 & O6 --> O7
    O1 & O3 --> S4 --> O8
    D1 & D2 --> O9
    O2 & O3 & D2 --> O10
```

---

## 技术选型说明

| 层 | 技术 | 原因 |
|----|------|------|
| **界面** | HTML + CSS + Vanilla JS | 零依赖，打开即用 |
| **计算** | 纯客户端 JavaScript | 无需服务器，隐私安全 |
| **八字算法** | tyme4ts（参考）或自研 | 开源库成熟，可自实现 |
| **星象数据** | 静态内置（简化模型） | MVP 用简化算法，V2 可接 API |
| **分享卡片** | Canvas API | 浏览器原生支持，无需第三方 |
| **数据存储** | 不存储任何用户数据 | 出生信息敏感，完全本地计算 |

---

## MVP 技术边界

```
✅ 做：纯浏览器端计算，不收集/存储用户数据
✅ 做：静态数据内置（星座表、生肖表、干支表、文案模板）
✅ 做：简化星象模型（基于当前日期的数学推算）
❌ 不做：后端服务器 / API / 数据库
❌ 不做：实时星象 API 调用
❌ 不做：用户账号/登录系统
❌ 不做：付费/订阅系统
```

---

*系统架构图 · 所有流程图已完成*
