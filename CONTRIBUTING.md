# CONTRIBUTING

## 工作流

`data/profile/` 是课程内容的**唯一创作源头**，同时产出两种格式：

```
<course>/lessonN-<slug>/
├── index.md              ← 人类可读：场景清单 + 依赖关系 + 验收标准
├── index.json            ← 机器可读：title / description / scenes[] / acceptance
├── 0X-<scene>.md         ← 单场景脚本（可选，人看的）
└── 0X-<scene>.json       ← 单场景数据（机器吃的）：title / description / steps[]
```

### 步骤

1. 在 `lessonN-<slug>/` 里写 Markdown（人看的）：`index.md` 写场景清单与验收标准，场景脚本写 `0X-<scene>.md`
2. 维护同目录的 JSON 与之同步（机器吃的）：`index.json` 与场景 `0X-<scene>.json`
3. 平台服务端直接加载 JSON 即可上架，无需二次录入
4. 如需 DAG 视图，由场景文件派生 `index.html`（生成产物，勿手改结构）

### 原则

- **单源**：内容只在 profile 里写一次，不分散到多个仓库
- **双格式**：Markdown 给人看，JSON 给机器吃
- **同步**：修改 Markdown 后记得更新对应的 JSON

## 提交

本仓库是一个**子模块**，改动按分层顺序提交并推送：先在 `data/profile` 内提交并推送，再在父仓库（`quanttide-course`）更新子模块指针。

课程与课时的目录命名、新增/迁移课程与课时的约定见 [AGENTS.md](AGENTS.md)。
