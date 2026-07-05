# Tw93：你不知道的 Agent：原理、架构与工程实践

---
type: source
source_type: article
source_url: https://tw93.fun/2026-03-21/agent.html
raw_file: Clippings/tw93.fun/agent/agent.md
author: Tw93
published: 2026-03-21T16:00:00+00:00
clipped: 2026-07-05
processed: 2026-07-05
tags: [Agent 工程, AI Coding, Harness, 上下文工程, 工具设计, 评测, OpenClaw]
status: processed
---

## One-Line Summary

Tw93 系统梳理 Agent 的控制流、Harness、上下文工程、工具设计、记忆、多 Agent、评测、追踪、安全和 OpenClaw 落地，核心判断是 Agent 能否跑稳更多取决于工程基础设施，而不只是模型能力。

## Key Points

- Agent Loop 本质是感知、决策、行动、反馈的循环；新能力通常通过工具、提示结构和状态外化叠加，而不是改主循环。
- Workflow 与 Agent 的区别在控制权：路径由代码预定义的是 Workflow，由 LLM 动态决策的是 Agent。
- Harness 比模型更关键，至少包括验收基线、执行边界、反馈信号和回退手段。
- 上下文工程要防 Context Rot，通过常驻层、按需加载、运行时注入、记忆层和系统层分离来提高信号质量。
- Skills 应按需加载，系统提示只保留索引；描述需要有触发条件、边界和反例。
- 工具设计应遵循 ACI：面向 Agent 目标，而不是底层 API；边界清晰、参数防错、错误可修复。
- 记忆不是事后补丁，需要区分工作记忆、程序性记忆、情景记忆和语义记忆，并设计整合和回退。
- 放开 Agent 自主度的顺序应是先 Harness，再回退能力，最后才是放权。
- 多 Agent 需要先有任务图、协议和隔离边界；子 Agent 只回传摘要，探索细节留在独立上下文。
- Agent 评测不能只看输出文本，也要看环境最终结果；Pass@k 与 Pass^k 分别服务能力边界和上线质量。
- Agent 追踪需要完整 Trace 和事件流，才能定位工具选择、上下文污染、绕圈和异常成本。
- OpenClaw 展示了这些原则如何落地为消息解耦、状态外化、分层提示、记忆整合和安全边界。

## Quotable Facts

- 文章发布时间为 2026-03-21。
- 原文包含 25 张图片，已下载到本地 `Clippings/tw93.fun/agent/media/`。
- 作者引用 OpenAI、Anthropic、LangChain、Cloudflare、Simon Willison 等资料作为参考。
- 作者将 Agent 常见反模式归纳为系统提示当知识库、工具数量失控、缺少验证机制、多 Agent 无边界、记忆不整合、没有评测、过早引入多 Agent、约束靠期望不靠机制。

## Entities

- People: `[[wiki/people/Tw93]]`
- Organizations:
- Products: `[[wiki/orgs/OpenClaw]]`
- Models: Claude Code、Codex、Opus
- Tools: Skills、MCP、Trace、MessageBus、MEMORY.md、AGENTS.md

## Topic Links

- `[[wiki/topics/Agent 工程]]`

## Contradictions Or Tensions

- 更强模型并不必然带来更稳定的 Agent；缺 Harness、评测和工具设计时，模型能力可能被基础设施问题抵消。
- 文档化约束易被 Agent 忽略，但编码化约束、Linter、Hook 和可执行验证能显著提高可靠性。
- 多 Agent 看似提升并行度，但在任务图、协议和隔离边界缺失时，会放大幻觉和协调成本。

## Follow-Up Questions

- 这个知识库本身是否应该把 `AGENTS.md` 控制在更短索引层，并把细节拆到 `docs/`？
- 我们是否要为 ingest、lint、digest 建立可执行检查清单或脚本，让约束从文档转为机制？
- `Agent 工程` 主题后续是否需要拆出独立页面：上下文工程、工具设计、Agent 评测、Agent 安全？

## Updates Made

- 创建 `[[wiki/topics/Agent 工程]]`。
- 创建 `[[wiki/orgs/OpenClaw]]`。
- 更新 `[[wiki/people/Tw93]]`。
- 更新 `index.md`、`log.md`、`AGENTS.md` 和 `README.md`。
