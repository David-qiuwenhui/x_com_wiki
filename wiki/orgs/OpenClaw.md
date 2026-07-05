# OpenClaw

---
type: project
tags: [Agent 工程, OpenClaw, AI Coding]
created: 2026-07-05
updated: 2026-07-05
source_count: 1
---

## Summary

OpenClaw 是 Tw93 文章中用来说明 Agent 工程原则如何落地的可运行系统案例。当前来源将它作为消息解耦、状态外化、分层提示、记忆整合、安全边界和长期运行机制的综合示例。

## Architecture Notes

- 整体可拆成 WebSocket 服务、渠道适配、消息总线、Agent Loop、上下文与记忆、工具与外部能力等层次。
- Channel 与 Agent 不直接通信，统一通过 MessageBus 解耦。
- AgentLoop 统一管理 session，渠道适配器只负责输入输出。
- 系统提示按层叠加，包括身份层、运行时层、记忆层、Skills 层和动态注入。
- 长任务通过文件系统状态恢复，避免依赖单次上下文窗口。

## Engineering Principles

- 先跑通单渠道最小闭环，再抽象多渠道。
- 记忆整合要早做，避免长对话后上下文质量下降。
- 第一个真实失败案例应尽快转成评测。
- 白名单、工作空间隔离和 source-sink 拆分是安全基础。

## Related People

- `[[wiki/people/Tw93]]`

## Related Topics

- `[[wiki/topics/Agent 工程]]`

## Sources

- `[[wiki/sources/2026-07-05-agent-architecture-engineering-practice]]`
