# MCP & Skills-based AI Memory

通过模型上下文协议 (MCP) 和特定助手技能（如 Moltbot Skills）增强大模型长期记忆的实现方案。

## MCP 方法项目 (Model Context Protocol)

| 项目名称 | 介绍 | GitHub 链接 |
| :--- | :--- | :--- |
| **meMCP** | Memory-Enhanced MCP，提供持久化语义搜索与 TF-IDF 索引。 | [mixelpixx/meMCP](https://github.com/mixelpixx/meMCP) |
| **memento-mcp** | 基于知识图谱的记忆系统，支持语义检索与时间感知。 | [gannonh/memento-mcp](https://github.com/gannonh/memento-mcp) |
| **mcp-memory** | Redis Graph 后端知识图谱服务器，存储复杂的项目与对话关系。 | [samwang0723/mcp-memory](https://github.com/samwang0723/mcp-memory) |
| **memory-mcp** | 简单的集成式 MCP 服务器，支持持久记忆与智能归档。 | [JamesANZ/memory-mcp](https://github.com/JamesANZ/memory-mcp) |

## Skills 方法项目 (Assistant Skills)

| 项目名称 | 介绍 | GitHub 链接 |
| :--- | :--- | :--- |
| **git-notes-memory** | 使用 Git-notes 在 Git 仓库级别实现跨会话持久记忆。 | [VoltAgent/awesome-moltbot-skills](https://github.com/VoltAgent/awesome-moltbot-skills) |
| **triple-memory** | LanceDB + Git-Notes + 文件三重记忆系统，专为 Moltbot 设计。 | [VoltAgent/awesome-moltbot-skills](https://github.com/VoltAgent/awesome-moltbot-skills) |
| **mcporter-skill** | 允许从 Moltbot 技能中调用远程 MCP 记忆服务的工具。 | [VoltAgent/awesome-moltbot-skills](https://github.com/VoltAgent/awesome-moltbot-skills) |

## 使用建议
1. **协议优先**：如果使用支持 MCP 的客户端（如 Claude Desktop），优先选择 **meMCP** 或 **memento-mcp**。
2. **深度集成**：Moltbot 用户可以通过 **molthub** 直接安装 Git-notes 基于的记忆插件，特别适合存储小说情节。
3. **架构参考**：优先测试从简单原子存储起步，根据准确率再决定是否引入 Redis Graph 等复杂后端。
