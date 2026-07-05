# X 信息阅读知识库

这个仓库按照 [LLM Wiki](llm-wiki.md) 方法论初始化，用来沉淀你从 x.com 阅读到的信息。核心原则是：原始材料保留不动，LLM 维护一个持续编译、交叉引用、可追溯的 Markdown wiki。

## 日常工作流

1. 用 Obsidian Web Clipper 将 x.com 内容保存到 `raw/x/`。
2. 如果页面有图片或附件，保存到 `raw/assets/`。
3. 让 Codex ingest 某个文件或一批文件。
4. Codex 会更新 `wiki/`、`index.md` 和 `log.md`。
5. 定期让 Codex 生成 `wiki/digests/` 摘要或运行 `wiki/lint/` 健康检查。

## 目录结构

- `raw/`: 原始材料层。这里的文件是来源真相，默认只读。
- `wiki/`: LLM 维护的知识层。这里存摘要、主题页、人物页、组织页、问题分析和周期 digest。
- `templates/`: ingest、主题页、digest 等页面模板。
- `index.md`: 内容索引，回答问题前优先阅读。
- `log.md`: 时间线日志，记录 ingest、query、lint 等操作。
- `AGENTS.md`: Codex 后续维护本库时必须遵守的操作规约。

## Obsidian 建议

- 将本目录作为 Obsidian vault 打开。
- Web Clipper 保存路径建议设为 `raw/x/`。
- 附件路径建议设为 `raw/assets/`。
- 使用双链时优先链接 `wiki/` 页面，不直接在 `raw/` 文件之间编织结构。

