# Agent Memory Tools & Frameworks

为个人 AI 助手（如 Moltbot）提供长期记忆的开源项目精选，主要通过向量数据库、知识化图谱或 LLM 框架集成。

## 核心推荐

| 项目名称 | 核心功能 | 存储类型 |
| :--- | :--- | :--- |
| **Mem0** | 多层次记忆、自适应个性化，支持高效检索和更新。 | 图形 + 向量 |
| **Letta (MemGPT)** | 构建有状态 AI 代理，透明的长期记忆管理。 | 图形 + 向量 |
| **Cognee** | 知识图谱 + 向量存储，提供动态语义记忆。 | 图形 + 向量 |
| **Zep AI** | 聊天记忆平台，支持自动总结和情感分析。 | 图形 + 向量 |
| **SimpleMem** | 终身记忆代理，支持跨对话项目历史。 | 向量 |
| **LlamaIndex** | 领先的 RAG 框架，提供多种记忆索引。 | 向量 + 图形 |
| **Qdrant** | 高性能向量数据库，适合大规模记忆存储。 | 向量 |

## 2026 新增（本地优先 / 跨工具）

| 项目名称 | 核心功能 | 存储类型 |
| :--- | :--- | :--- |
| **Memorix** | 本地优先的共享记忆层，跨 Claude Code / Codex / Cursor / OpenCode 等宿主共享同一项目记忆。 | 本地文件 + MCP |
| **mcp-memory (OKF)** | 以 Open Knowledge Format v0.2 Markdown + SQLite FTS5 存储，记忆可读、可审计、可版本化。 | SQLite + Markdown |
| **Memstate** | MCP 记忆服务，主打多会话编码场景的冲突检测与决策追踪。 | 托管 + MCP |

## 集成建议
1. **优先选择**：Mem0 或 Letta 是专为 AI Agent 设计的。
2. **渐进式集成**：建议从向量存储起步，待业务复杂后再引入图谱。
3. **框架支持**：利用 LlamaIndex 等框架可以快速在 Python/TS 环境中扩展记忆功能。
4. **编码 agent / 多工具协同**：优先本地优先方案（Memorix、Basic Memory），避免记忆被单一宿主锁定。
