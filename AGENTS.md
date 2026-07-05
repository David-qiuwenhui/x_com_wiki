# AGENTS.md

本仓库是一个面向 x.com 阅读整理的 LLM Wiki。Codex 的职责是维护 `wiki/` 层，而不是改写原始资料。

## 核心原则

- `raw/` 和 `Clippings/` 是原始来源层，除非用户明确要求清理或迁移，不修改其中内容。
- `wiki/` 是 LLM 生成和维护的知识层，可以创建、重写、合并、拆分页面。
- 每次 ingest 都要更新 `index.md` 和 `log.md`。
- 每个重要事实、观点或判断都要能追溯到 `raw/`、`Clippings/` 来源或 `wiki/sources/` 来源页。
- 当新来源和旧结论冲突时，不要静默覆盖；在相关页面标注分歧、时间和来源。
- 优先使用 Obsidian 双链，例如 `[[wiki/topics/AI Agents]]`。

## 目录约定

- `Clippings/`: 用户当前使用的 Obsidian Web Clipper 原始语料目录，优先视为 x.com 剪藏入口。
- `raw/x/`: 备用的 x.com 推文、thread、article、profile 或搜索结果原始语料目录。
- `raw/assets/`: Web Clipper 下载的图片和附件。
- `wiki/sources/`: 每个原始来源对应的消化页。
- `wiki/topics/`: 可持续更新的主题页。
- `wiki/people/`: 人物页，记录身份、观点、相关内容和可信度线索。
- `wiki/orgs/`: 公司、团队、项目、机构页面。
- `wiki/digests/`: 每日、每周、每月或专题摘要。
- `wiki/questions/`: 用户提出的问题、比较、分析和结论页。
- `wiki/lint/`: 健康检查报告。
- `templates/`: 页面模板。

## 命名规范

- 原始剪藏保留 Web Clipper 生成的文件名即可。
- 来源消化页使用 `YYYY-MM-DD-short-title.md`。
- 主题页使用可读标题，例如 `AI Agents.md`、`Open Models.md`。
- 人物页使用公开名称或 handle，例如 `Andre Karpathy.md`、`sama.md`。
- Digest 使用 `YYYY-MM-DD-daily.md`、`YYYY-W27-weekly.md` 或 `YYYY-MM-monthly.md`。

## Ingest 流程

用户要求 ingest 一个或多个 `Clippings/` 或 `raw/x/` 文件时：

1. 阅读原始文件，保留原文语境，不凭空补充来源中没有的信息。
2. 在 `wiki/sources/` 创建或更新对应来源页，优先使用 `templates/source-note.md`。
3. 提取可复用信息：
   - 核心观点
   - 可引用事实
   - 人物、组织、产品、论文、模型、工具
   - 主题标签
   - 与既有 wiki 页面的关系
   - 可能的矛盾或待验证点
4. 更新相关 `wiki/topics/`、`wiki/people/`、`wiki/orgs/` 页面。
5. 如内容适合周期回顾，更新或创建 `wiki/digests/` 页面。
6. 更新 `index.md`。
7. 在 `log.md` 追加一条 `ingest` 记录。

## URL 抓取流程

- 用户提供网页链接并要求整理时，先将网页保存为 `Clippings/` 下的原始 Markdown 语料。
- 默认下载网页图片和视频到 `Clippings/` 相邻目录，保证本地可复查。
- `Clippings/` 不纳入 git，因此下载的原文和媒体只在本地保留。
- 抓取后必须检查标题、正文长度和关键章节，避免只保存到导航、错误页或空壳页面。
- 通过质量检查后，再按 Ingest 流程更新 `wiki/`、`index.md` 和 `log.md`。

## Git 与发布策略

- 每次完成 ingest、digest、lint 或结构性维护后，都应创建一个语义清晰的本地 commit。
- `Clippings/` 默认只在本地保留，不纳入 git，不推送到公开仓库。
- 公开仓库默认只保存 `wiki/`、`index.md`、`log.md`、模板和项目规约。
- push 前必须检查提交范围，确认没有把原始语料、隐私信息或不适合公开的内容发布出去。
- 如用户明确要求公开某些原始语料，才可以把对应文件加入 git。

## Query 流程

用户提问时：

1. 先阅读 `index.md` 判断相关页面。
2. 再阅读必要的 `wiki/` 页面和来源页。
3. 回答中区分：
   - 已有来源支持的结论
   - 来自多个页面的综合判断
   - 需要新来源验证的推测
4. 如果回答形成了有长期价值的分析，询问或直接按用户意图保存到 `wiki/questions/`，并更新 `index.md`、`log.md`。

## Digest 流程

生成 digest 时：

1. 确定时间范围和纳入来源。
2. 聚合来源页，而不是只看原始剪藏。
3. 输出主要趋势、反复出现的主题、重要人物/组织、待跟进问题。
4. 对每条关键判断提供来源链接。
5. 保存到 `wiki/digests/` 并更新索引和日志。

## Lint 流程

用户要求健康检查时，检查：

- `wiki/` 中没有被 `index.md` 收录的页面。
- 重要概念被多次提到但没有主题页。
- 主题页缺少来源链接。
- 新旧页面之间存在矛盾但未标注。
- 存在孤立页面、重复页面或过时页面。
- `log.md` 和实际文件状态不一致。

检查结果保存到 `wiki/lint/YYYY-MM-DD-lint.md`。

## 写作风格

- 使用中文为主，保留英文专有名词。
- 摘要要短，综合页可以逐步增长。
- 明确标注不确定性，不把观点写成事实。
- 不为追求完整性制造空洞栏目；没有信息就省略或标注“尚无来源”。
