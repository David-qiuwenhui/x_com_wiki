# Agent 工程

---
type: topic
tags: [Agent 工程, AI Coding, Harness, 上下文工程, 工具设计, 评测]
created: 2026-07-05
updated: 2026-07-05
source_count: 1
---

## Summary

Agent 工程的核心不是把一个 ReAct Loop 写复杂，而是围绕稳定循环建设 Harness、上下文工程、工具设计、记忆、评测、追踪、安全边界和状态外化。当前来源强调：能否稳定落地，往往取决于工程基础设施和验证质量，而不只是模型能力。

## Current Claims

- Agent Loop 的核心控制流相对稳定，新能力应优先通过工具扩展、提示结构和状态外化加入。
- Workflow 与 Agent 的关键区别是控制权归属：预设流程属于 Workflow，LLM 动态决策才是 Agent。
- Harness 至少包括验收基线、执行边界、反馈信号和回退手段，是 Agent 成功率的基础。
- 上下文工程应按常驻层、按需加载、运行时注入、记忆层、系统层分层，避免 Context Rot。
- Skills 应延迟加载，系统提示保留索引，完整知识按需读取。
- 工具设计应从 API Interface 转为 Agent-Computer Interface，面向 Agent 目标而非底层端点。
- 记忆系统需要区分工作记忆、程序性记忆、情景记忆和语义记忆，并支持整合与回退。
- 多 Agent 应先建立任务图、协议和隔离边界，再谈并行。
- 评测要同时覆盖执行记录和环境结果，先修评测再改 Agent。
- Trace 和事件流是排查 Agent 行为的前提。

## Open Questions

- 对个人知识库维护 Agent 来说，哪些约束应该从 `AGENTS.md` 下沉成脚本或检查？
- 当前 `wiki/` 规模何时需要从 `index.md` 升级到本地搜索或 MCP 搜索？
- ingest 工作流是否应该引入“来源质量检查”和“公开前检查”的自动化脚本？

## Contradictions Or Debates

- 长上下文看似增强能力，但无关信息过多会稀释关键信号。
- 多 Agent 看似提高吞吐，但缺协议和隔离时可能放大错误。
- 文档规则能表达意图，但真正可靠的约束需要工具验证、Linter、Hook 或测试。

## Related People

- `[[wiki/people/Tw93]]`

## Related Organizations And Projects

- `[[wiki/orgs/OpenClaw]]`

## Sources

- `[[wiki/sources/2026-07-05-agent-architecture-engineering-practice]]`
