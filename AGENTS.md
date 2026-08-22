# AGENTS.md — 课程开发工作指南

本文档为在 **quanttide-profile-of-course-development**（课程开发档案，即 `data/profile`）中工作的 Agent 与协作者提供指南。它是课程内容的**唯一创作源头**。

## 仓库定位

- **单一创作源头**：课程内容只在 `data/profile` 写一次，不分散到多个仓库。
- **单源双格式**：Markdown 给人看（`index.md`、场景 `.md`）、JSON 给机器吃（`index.json`、场景 `.json`），平台服务端直接加载 JSON 上架，无需二次录入。
- **同步原则**：修改 Markdown 后记得同步对应的 JSON。

## 课时组织约定

```
<course>/                       # 一门课程，如 production-internship / vibe-coding
├── README.md                   # 课程说明（可为占位）
└── lessonN-<slug>/             # 一个课时，N 为课时序号，slug 为英文短名
    ├── index.md                # 人类可读：场景清单 + 依赖关系
    ├── index.json              # 机器可读：title / description / scenes[{title, description, exception}]
    ├── 0X-<scene>.json         # 单场景：title / description / steps[{title, description}]
    └── index.html              # 由场景文件派生的 DAG 视图（生成产物，勿手改结构，只可同步标题字符串）
```

目录名用**英文小写连字符**（如 `lesson1-second-brain`），与既有 `lesson1-setup`、`lesson2-feishu` 一致。课程名用英文（如 `production-internship`）。

## 课程研发策略

以生产实习课程为中心的研发策略（中心 → 输出 → 降级、边界原则、教学对象口径）见 [index.md](index.md)。本文档只保留在本仓库工作的操作约定。

## 关键文档索引

| 文档 | 用途 |
|------|------|
| [index.md](index.md) | 以生产实习为中心的课程研发策略（中心 → 输出 → 降级、边界原则） |
| [CONTRIBUTING.md](CONTRIBUTING.md) | 工作流、单源双格式、同步原则 |
| [README.md](README.md) | 仓库简介、课程蓝图索引 |
| [vibe-coding/](vibe-coding/) | 氛围编程课程（课时示例：lesson1-setup、lesson2-feishu） |
| [production-internship/](production-internship/) | 生产实习课程（课时1 第二大脑、课时2 版本发布） |

## 常见任务速查

- **新增课程**：建英文目录 + `README.md` 占位。
- **新增课时**：建 `lessonN-<slug>/`，写 `index.md` + `index.json`；如需 DAG 视图再补 `index.html`。
- **迁移课时**：用 `git mv` 保留历史；若目标课程编号已到，重命名为新序号（如 `lesson1-release` → `lesson2-release`）。
- **提交**：遵循 [CONTRIBUTING.md](CONTRIBUTING.md)（单源、双格式、同步）；本仓库本身是一个子模块，改完需在子模块内提交并按分层规范（子模块→父仓库→更外层）更新指针并推送。
