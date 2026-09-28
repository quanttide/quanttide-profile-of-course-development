# CONTRIBUTING

本仓库是课程内容的唯一创作源头。本文约定内容的结构、基本动作与验收标准。

## 结构

内容按课程、课时、场景、步骤逐级包含：一门课程（course）下含若干课时（lesson），一个课时含若干场景（scene），一个场景含若干步骤（step）。课时归属于课程，课时序号在课程内唯一。

```
<course>/                       # 一门课程，如 software-engineering
├── README.md                   # 课程说明，可为占位
└── lessonN-<slug>/             # 课时，N 为课时序号，slug 为英文短名
    ├── index.md                # 场景清单、依赖关系、验收标准
    ├── index.json              # 机器可读：title / description / scenes[{title, description, exception}] / acceptance{criteria, method, on_fail}
    ├── 0X-<scene>.md           # 场景脚本，可选
    ├── 0X-<scene>.json         # 场景数据：title / description / steps[{title, description}]
    └── index.html              # 场景 DAG 视图，生成产物，勿手改结构
```

课程名与课时 slug 均用英文小写连字符。课时序号 `N` 从 1 递增，在所属课程内唯一。

## 基本动作

### 新增课程

在根目录建英文目录，并放 `README.md` 占位。

### 新增课时

在课程目录下建 `lessonN-<slug>/`，写 `index.md` 与 `index.json`；需要 DAG 视图时再补 `index.html`。`N` 取课程内的下一个序号。

### 编辑内容

内容只在 `data/profile` 写一次，产出两种格式：Markdown 给人看，JSON 给机器吃，平台服务端直接加载 JSON 上架。修改 `index.md` 或 `0X-<scene>.md` 后，同步更新对应的 `index.json` 或 `0X-<scene>.json`，保持标题、场景、步骤与验收标准一致。

### 迁移课时

跨课程移动课时用 `git mv` 保留历史，移入后课时序号重置为目标课程内的序号，例如从 `lesson3-github` 移入空课程即为 `lesson1-github`。迁移改变课时所属的课程，重命名只改 slug，两者不要混淆。

### 提交

先在 `data/profile` 内提交改动并推送到远端，再在 `quanttide-course` 更新子模块指针，提交并推送。

## 验收标准

贡献被接受需满足以下条件。

- 目录与命名符合结构约定，课时序号在课程内连续唯一。
- 每个课时的 `index.md` 与 `index.json` 内容一致，包括标题、场景与验收标准。
- 每个课时有验收标准（`acceptance` 的 `criteria`、`method`、`on_fail`），每个场景有异常分支（`exception`）。
- 若存在 `index.html`，其标题字符串与 `index.md` 同步。
