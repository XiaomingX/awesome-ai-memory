# awesome-ai-memory - A list of AI memory projects (Updated 2026)

| 名称 | 网址 | 类型 | GitHub 网址 | 分类 | 存储类型 |
| --- | --- | --- | --- | --- | --- |
| **Mem0** | [https://mem0.ai/](https://mem0.ai/) | 托管，开源 | [https://github.com/mem0ai/mem0](https://github.com/mem0ai/mem0) | 记忆层 | 图形，向量 |
| **Graphiti** (Zep Core) | [https://www.getzep.com/](https://www.getzep.com/) | 开源，托管 | [https://github.com/getzep/graphiti](https://github.com/getzep/graphiti) | 记忆层 | 时序知识图谱 |
| **LangMem** | [https://langchain-ai.github.io/langmem/](https://langchain-ai.github.io/langmem/) | 开源 | [https://github.com/langchain-ai/langmem](https://github.com/langchain-ai/langmem) | 记忆层 | 向量，图形 |
| **Cognee** | [https://www.cognee.ai/](https://www.cognee.ai/) | 托管，开源 | [https://github.com/topoteretes/cognee](https://github.com/topoteretes/cognee) | 记忆工具 | 图形，向量 |
| **Basic Memory** | [https://basicmachines.co/](https://basicmachines.co/) | 本地优先，开源 | [https://github.com/basicmachines-co/basic-memory](https://github.com/basicmachines-co/basic-memory) | 本地存储 (MCP) | Markdown + SQLite |
| **Nano-GraphRAG** | - | 开源 | [https://github.com/gusye1234/nano-graphrag](https://github.com/gusye1234/nano-graphrag) | 记忆工具 | 图形，向量 |
| **AgentCortex** | [https://agentcortex.dev/](https://agentcortex.dev/) | 开源 | [https://github.com/sage-hq/agentcortex-mcp](https://github.com/sage-hq/agentcortex-mcp) | 记忆工具 (MCP) | 向量 |
| **Letta** (原 MemGPT) | [https://letta.com/](https://www.google.com/search?q=https://letta.com/) | 托管，开源 | [https://github.com/letta-ai/letta](https://github.com/letta-ai/letta) | 记忆工具 | 图形，向量 |
| **Memary** | [https://finetune.dev/](https://finetune.dev/) | 开源 | [https://github.com/kingjulio8238/Memary](https://github.com/kingjulio8238/Memary) | 记忆工具 | 图形 |
| **GraphRAG** (微软) | [https://microsoft.github.io/graphrag/](https://microsoft.github.io/graphrag/) | 开源 | [https://github.com/microsoft/graphrag](https://github.com/microsoft/graphrag) | 记忆工具 | 图形，向量 |
| **Memories.ai** | [https://memories.ai/](https://memories.ai/) | 托管 | - | 记忆增强 | 视频+向量 |
| **Chroma** | [https://www.trychroma.com/](https://www.trychroma.com/) | 开源 | [https://github.com/chroma-core/chroma](https://github.com/chroma-core/chroma) | 向量数据库 | 向量+元数据 |
| **Milvus** | [https://milvus.io/](https://milvus.io/) | 开源 | [https://github.com/milvus-io/milvus](https://github.com/milvus-io/milvus) | 向量数据库 | 向量+元数据 |
| **Weaviate** | [https://weaviate.io/](https://weaviate.io/) | 开源 | [https://github.com/weaviate/weaviate](https://github.com/weaviate/weaviate) | 向量数据库 | 向量+元数据 |
| **Qdrant** | [https://qdrant.tech/](https://qdrant.tech/) | 开源 | [https://github.com/qdrant/qdrant](https://github.com/qdrant/qdrant) | 向量数据库 | 向量+元数据 |
| **Neo4j** | [https://neo4j.com/](https://neo4j.com/) | 托管，开源 | [https://github.com/neo4j](https://github.com/neo4j) | 图数据库 | 图形 |
| **OpenMemory** | - | 协议标准 | [https://github.com/mem0ai/mem0](https://github.com/mem0ai/mem0) | 记忆协议 | - |

---

# 开源AI记忆列表优化更新建议（2025-2026版）

结合2025年以来的最新开源动态，以下为对`awesome-ai-memory`列表的深度优化与更新说明。本次更新重点关注**MCP（Model Context Protocol）生态**、**知识图谱轻量化**以及**官方框架的记忆层**。

## 一、 关键更新与新增项目

1. **Zep 升级为 Graphiti**：
* **更新说明**：Zep 团队已将其核心的时序知识图谱引擎开源为 **Graphiti**。相比原有的 Zep 服务，Graphiti 更强调作为开发者的底层构建块，支持构建动态的、随时间变化的知识图谱记忆，是目前构建复杂 Agent 记忆的首选之一。


2. **新增 LangMem (LangChain 官方)**：
* **新增理由**：LangChain 官方推出的长期记忆解决方案。它通过后台进程自动提取、整合和更新 Agent 的知识，弥补了此前 LangChain 生态中缺乏标准化长期记忆层（Long-term Memory Layer）的空白。


3. **修正 Basic Memory**：
* **修正说明**：将链接修正为 `basicmachines-co/basic-memory`。这是一个基于 **MCP (Model Context Protocol)** 的本地化记忆服务，它允许 AI 直接读写本地 Markdown 文件并建立关联，非常适合 Obsidian 用户和注重隐私的本地 Agent 开发。


4. **新增 Nano-GraphRAG**：
* **新增理由**：微软的 GraphRAG 虽然强大但资源消耗巨大。**Nano-GraphRAG** 是一个极轻量级、易于修改的实现，它保留了图检索的核心优势，但大幅降低了部署门槛，适合个人开发者和中小型项目。


5. **新增 AgentCortex**：
* **新增理由**：首个原生的 **MCP** 记忆系统。随着 Anthropic 推出的 MCP 协议成为连接 LLM 与本地数据的标准，AgentCortex 提供了一种开箱即用的方式，让 Cursor、Claude Desktop 等工具拥有持久化记忆。



## 二、 移除或降级建议

1. **移除/归档 AutoGPT**：
* 虽然 AutoGPT 是 Agent 的先驱，但其内存管理较为初级。在“AI 记忆”这个特定主题下，它不如专门的记忆层工具（如 Mem0, Letta）具有代表性。建议将其归类为“Agent 框架”而非“记忆项目”。


2. **合并 OpenMemory MCP**：
* OpenMemory 目前主要由 Mem0 推动，建议在 Mem0 条目中备注即可，无需作为独立项目列出，除非有其他厂商跟进该特定协议。



## 三、 选型建议更新

1. **生产环境首选**：构建面向用户的商业应用，优先考虑 **Mem0**（多用户管理成熟）或 **Graphiti**（图谱结构化能力强）。
2. **框架原生开发**：如果你使用 LangChain/LangGraph 开发，直接集成 **LangMem** 是最顺畅的路径。
3. **本地与隐私场景**：对于个人知识库助手或本地 LLM，**Basic Memory** 和 **Nano-GraphRAG** 是最佳选择，前者易于管理（Markdown），后者检索效果好。
4. **MCP 生态集成**：如果你正在为 Claude Desktop 或 Cursor 开发插件，请关注 **AgentCortex** 和 **Basic Memory** 的 MCP 接口。
