# Claude & Codex 对话记录归档

自动扫描 D盘和E盘，归档所有 Claude Code 和 Codex 的聊天记录，并提供可视化看板浏览。

## 项目结构

```
D:\对话记录-cc-codex\
│
├── README.md                    ← 本文件
├── index.html                   ← 旧版看板（纯HTML，双击直接打开）
├── data.json                    ← 提取的对话元数据（JSON格式）
│
├── antd-dashboard\              ← 新版看板（Ant Design美化版）
│   ├── index.html               ← 看板入口
│   ├── data.json                ← 对话数据
│   ├── assets\
│   │   ├── index-DL8FlzpA.js    ← React + Ant Design 打包产物
│   │   └── index-DARBCN6e.css   ← 样式
│   ├── favicon.svg
│   └── icons.svg
│
├── claude-code\                 ← Claude Code 对话记录
│   │
│   ├── claude-home-projects\    ← 来源: C:\Users\Administrator\.claude\projects\
│   │   ├── C--Users-Administrator\        ← C盘用户目录项目 (4条)
│   │   │   ├── 0a6cdeb4-....jsonl
│   │   │   ├── 5f7cbfd4-....jsonl
│   │   │   ├── 888a9492-....jsonl
│   │   │   └── 98edfa43-....jsonl
│   │   │
│   │   ├── E--AI-TestProject-v2\          ← E盘TestProject-v2项目 (5条主对话)
│   │   │   ├── 16e69669-....jsonl
│   │   │   ├── 4530697c-....jsonl
│   │   │   ├── 9a6e9f2f-....jsonl
│   │   │   ├── a8306e90-....jsonl
│   │   │   ├── eb7e8502-....jsonl
│   │   │   └── subagents\                 ← 子Agent对话 (14条)
│   │   │       ├── agent-a290e15d-....jsonl
│   │   │       └── ...
│   │   │
│   │   └── E--CC-test\                    ← E盘CC-test项目 (1条)
│   │       └── eaec11af-....jsonl
│   │
│   ├── CC-test-projects\        ← 来源: E:\CC-test\.claude\projects\
│   │   ├── C--Users-Administrator--claude-mimo\  ← Mimo项目 (4条)
│   │   │   ├── 6a963594-....jsonl
│   │   │   ├── c27afb71-....jsonl
│   │   │   ├── daef31dc-....jsonl
│   │   │   └── de8c10d5-....jsonl
│   │   │
│   │   └── E--CC-test\                    ← CC-test项目对话 (10条)
│   │       ├── 1d7fabf7-....jsonl
│   │       ├── 360b428a-....jsonl
│   │       ├── 6d9a9dbc-....jsonl
│   │       ├── 90864287-....jsonl
│   │       ├── 9620c79a-....jsonl
│   │       ├── 9ef9c38e-....jsonl
│   │       ├── a2554495-....jsonl
│   │       ├── c058ba70-....jsonl
│   │       ├── c8085b34-....jsonl
│   │       └── db3f6604-....jsonl
│   │
│   └── sessions\                ← Claude会话元数据 (4条)
│       ├── 10932.json
│       ├── 15664.json
│       ├── 21336.json
│       └── 21900.json
│
└── codex\                       ← Codex (OpenAI) 对话记录
    ├── history.jsonl            ← Codex历史记录 (220条，14个session)
    └── logs_2.sqlite            ← Codex日志数据库 (271MB)
```

## 文件说明

| 文件 | 说明 | 大小 |
|------|------|------|
| `index.html` | 旧版看板，纯HTML+CSS+JS，双击浏览器直接打开 | 82KB |
| `antd-dashboard/` | 新版看板，基于Ant Design 6 + React 19，暗色主题 | 970KB |
| `data.json` | 提取的对话元数据，包含关键词、摘要、时间等 | 43KB |
| `claude-code/*.jsonl` | Claude Code对话的原始JSONL格式记录 | 15MB |
| `codex/history.jsonl` | Codex对话历史，每行一条消息 | 221KB |
| `codex/logs_2.sqlite` | Codex完整日志数据库 | 271MB |

## 数据统计

- **总对话数**: 58条
  - Claude Code: 44条（含14条子Agent）
  - Codex: 14条（按session分组）
- **涉及项目**: 4个
  - E盘-TestProject-v2（B2B线索研究项目）
  - E盘-CC-test（测试项目）
  - C盘-用户目录（全局配置）
  - Codex对话

## 使用方式

### 旧版看板（推荐快速查看）
直接双击 `index.html`，用浏览器打开即可。无需服务器。

### 新版看板（推荐正式使用）
需要本地HTTP服务器：
```bash
cd D:\对话记录-cc-codex\antd-dashboard
python -m http.server 8766
# 打开 http://localhost:8766
```

或使用源码开发模式：
```bash
cd D:\antd-components
npm run dev
# 打开 http://localhost:5173
```

## 看板功能

| 功能 | 旧版 | 新版 |
|------|------|------|
| 对话列表展示 | ✓ | ✓ |
| 关键词标签 | ✓ | ✓（彩色Tag） |
| 按类型筛选 | ✓ | ✓ |
| 按项目筛选 | ✓ | ✓ |
| 关键词搜索 | ✓ | ✓ |
| 列排序 | ✓ | ✓ |
| 一键复制路径 | ✓ | ✓ |
| 备注功能 | ✓（localStorage） | ✓（localStorage） |
| 暗色主题 | ✓ | ✓ |
| 统计卡片 | ✓ | ✓（动态） |
| 分页 | - | ✓ |
| 响应式布局 | - | ✓ |

## 数据来源路径

| 原始路径 | 对应归档目录 |
|----------|-------------|
| `C:\Users\Administrator\.claude\projects\` | `claude-code\claude-home-projects\` |
| `E:\CC-test\.claude\projects\` | `claude-code\CC-test-projects\` |
| `C:\Users\Administrator\.codex\` | `codex\` |

## 技术栈

- **旧版看板**: 纯HTML/CSS/JavaScript，无依赖
- **新版看板**: React 19 + Ant Design 6 + Vite 8 + TypeScript 6
- **数据提取**: Python 3（JSONL解析 + 关键词提取）
