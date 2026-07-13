# CONTRIBUTING

## 工作流

`data/profile/` 是课程内容的**唯一创作源头**，同时产出两种格式：

```
vibe-coding/
├── lesson1.json       ← 机器可读，对接平台服务端 API
└── lesson1/
    ├── index.md       ← 人类可读，视频脚本/文档
    ├── sense1.md
    ├── sense2.md
    └── ...
```

### 步骤

1. 在 `lesson1/` 里写 Markdown 脚本（人看的）
2. 维护 `lesson1.json` 与之同步（机器吃的）
3. 平台服务端直接加载 JSON 即可上架，无需二次录入

### 原则

- **单源**：内容只在 profile 里写一次，不分散到多个仓库
- **双格式**：Markdown 给人看，JSON 给机器吃
- **同步**：修改 Markdown 场景后记得更新对应的 JSON
