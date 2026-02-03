# Awesome AI Memory - 长期记忆项目精选列表 (2026 版)

这是一个专注于大语言模型 (LLM) 长期记忆 (Long-term Memory) 实现的精选列表。涵盖了从上层聚合记忆层、Agent 记忆工具到基础存储设施的完整生态。

## 🚀 核心更新 (2025-2026)
*   **MemAlign (2026-02)**: Databricks 发布的基于人类反馈对齐的轻量级双记忆系统。
*   **叙事增强**: 引入针对长篇写作和叙事连贯性的专项记忆算法与工具。
*   **MCP 生态**: 涌现了大量支持 Cursor 和 Claude Desktop 的本地优先记忆插件。

---

## 🏗️ 1. 聚合记忆层 (Integrated Memory Layers)
这类项目提供逻辑复杂的记忆管理，支持多用户、多会话、自动摘要和知识提取。

| 名称 | GitHub 网址 | 类型 | 存储类型 | 特点 |
| :--- | :--- | :--- | :--- | :--- |
| **Mem0** | [mem0ai/mem0](https://github.com/mem0ai/mem0) | 托管/开源 | 图形 + 向量 | 智能记忆层，已整合 OpenMemory 协议，支持跨用户/会话记忆。 |
| **Memobase** | [memodb-io/memobase](https://github.com/memodb-io/memobase) | 开源 | Profile-based | 专注于事件演化和人物画像的长期记忆管理。 |
| **Graphiti**| [getzep/graphiti](https://github.com/getzep/graphiti) | 开源 | 时序知识图谱| Zep Core 开源版，专注随时间演变的动态关联知识存储。 |
| **LangMem** | [langchain-ai/langmem](https://github.com/langchain-ai/langmem) | 开源 | 向量 + 属性 | LangChain 官方长期记忆，自动提取、整合并更新知识。 |
| **MemAlign** | [mlflow/memalign](https://github.com/mlflow/memalign) | 开源 | 双记忆 | Databricks 2026 新作，通过双记忆系统对齐 LLM Judge。 |
| **Zep AI** | [getzep/zep](https://github.com/getzep/zep) | 托管/开源 | 图形 + 向量 | 聊天记忆平台，提供情感分析与深度总结功能。 |
| **Letta** | [letta-ai/letta](https://github.com/letta-ai/letta) | 托管/开源 | 分层存储 | 原 MemGPT，将记忆视为操作系统的多级缓存（RAM/Disk）。 |

---

## 🛠️ 2. Agent 与本地记忆工具 (Agentic & Local Tools)
适合个人开发者、单机 Agent 或集成到特定办公流程的项目。

| 名称 | GitHub 网址 | 类型 | 特点 |
| :--- | :--- | :--- | :--- |
| **NovelGenerator** | [KazKozDev/NovelGenerator](https://github.com/KazKozDev/NovelGenerator) | 多代理 | 跟踪人物视角、情节线与情感弧，适合生成完整小说。 |
| **AgentCortex**| [sage-hq/agentcortex-mcp](https://github.com/sage-hq/agentcortex-mcp) | MCP | 原生 MCP 记忆系统，支持 Cursor 和 Claude Desktop。 |
| **Basic Memory** | [basicmachines-co/basic-memory](https://github.com/basicmachines-co/basic-memory) | MCP/SQLite | 基于 SQLite 和 Markdown，极其隐私友好，适合本地知识库。 |
| **Nano-GraphRAG**| [gusye1234/nano-graphrag](https://github.com/gusye1234/nano-graphrag) | 本地优化 | 极轻量级 GraphRAG 实现，适合资源受限环境。 |
| **SimpleMem** | [aiming-lab/SimpleMem](https://github.com/aiming-lab/SimpleMem) | 开源 | 终身记忆层，支持跨对话的项目历史记忆。 |
| **Supermemory** | [supermemory-ai/supermemory](https://github.com/supermemory-ai/supermemory) | 云原生 | 基于 Cloudflare 生态，构建分布式的个人 AI 记忆大脑。 |
| **Khoj** | [khoj-ai/khoj](https://github.com/khoj-ai/khoj) | 多端 | 个人 AI 副驾驶，深度集成 Markdown 文档与笔记。 |

---

## 🤖 3. 框架集成 (AI Frameworks with Memory Support)
深度集成了长期记忆管理能力的通用 AI 开发框架。

| 名称 | GitHub 网址 | 核心能力 |
| :--- | :--- | :--- |
| **LlamaIndex** | [run-llama/llama_index](https://github.com/run-llama/llama_index) | 提供 Property Graph Index 和多种叙事增强的索引模式。 |
| **LangChain** | [langchain-ai/langchain](https://github.com/langchain-ai/langchain) | 内置多种 Memory 组件，支持与各类向量库无缝对接。 |

---

## 💾 4. 基础设施与存储 (Infrastructure & Storage)
为上述记忆层提供物理支撑的基础数据库。

| 分类 | 推荐项目 | 核心能力 |
| :--- | :--- | :--- |
| **向量数据库** | [Chroma](https://github.com/chroma-core/chroma), [Milvus](https://github.com/milvus-io/milvus), [Qdrant](https://github.com/qdrant/qdrant), [Weaviate](https://github.com/weaviate/weaviate) | 高效的语义相似度搜索与混合检索。 |
| **图数据库** | [Neo4j](https://github.com/neo4j) | 复杂的实体关系推理与深度关联分析。 |

---

## 💡 5. 选型与集成建议 (Practical Integration)

1. **从小处着手**：建议初学者从**向量数据库**开始。除非业务需要（如复杂的情节线推理），否则避免过早引入复杂的图谱结构。
2. **长篇叙事 (Storytelling)**：
   * 优先使用 **Mem0** 或 **NovelGenerator** 跟踪人物弧线。
   * **策略建议**：先生成并存储章节摘要，在生成新章节前检索摘要以保证连贯性。
3. **生态兼容性**：
   * 个人助手（如 **Moltbot**）与 **molthub** 用户建议使用提供成熟 SDK 的 Mem0 或 Letta。
4. **隐私敏感**：本地 Agent 首选 **Basic Memory** 或 **AgentGortex**。

---

## 🔬 6. 预训练与架构增强 (Research & Architecture)
专注于在训练阶段或架构层面提升 LLM 记忆能力的先进研究。

| 名称 | GitHub 网址 | 焦点内容 |
| :--- | :--- | :--- |
| **Titans** | [google-research/titans](https://github.com/google-research/titans) | Google 提出的经由神经记忆模块提升长文本处理的架构。 |
| **HOMER** | [alinlab/HOMER](https://github.com/alinlab/HOMER) | 层次上下文合并（ICLR 2024），高效扩展上下文长度。 |
| **Awesome LLM Pre-training** | [RUCAIBox/awesome-llm-pretraining](https://github.com/RUCAIBox/awesome-llm-pretraining) | 预训练策略、架构改进（如 Ultra-Sparse Memory）研究精选。 |

---

## 🔌 7. MCP 与 技能插件 (MCP & Assistant Skills)
利用模型上下文协议 (MCP) 或特定工具调用（Skills）为模型注入持久记忆的能力。

| 名称 | GitHub 网址 | 类型 | 特点 |
| :--- | :--- | :--- | :--- |
| **meMCP** | [mixelpixx/meMCP](https://github.com/mixelpixx/meMCP) | MCP | 提供持久化语义搜索、TF-IDF 索引及原子存储管理。 |
| **memento-mcp** | [gannonh/memento-mcp](https://github.com/gannonh/memento-mcp) | MCP | 知识图谱驱动的记忆系统，支持语义检索与时间感知。 |
| **Moltbot Skills**| [VoltAgent/awesome-moltbot-skills](https://github.com/VoltAgent/awesome-moltbot-skills) | Skills | 包含 Git-notes 记忆、LanceDB 三重记忆等 Moltbot 专属技能。 |
| **mcp-memory** | [samwang0723/mcp-memory](https://github.com/samwang0723/mcp-memory) | MCP/Redis | 使用 Redis Graph 作为后端的知识图谱 MCP 服务器。 |

---

## 🎨 8. 多模态一致性与记忆 (Multimodal Consistency & Memory)
在生成图像和视频时维持角色形象、画风及音色一致性的专用工具与算法。

| 分类 | 推荐项目 | GitHub 网址 | 核心特性 |
| :--- | :--- | :--- | :--- |
| **视觉一致性** | **StoryMaker**, **IP-Adapter** | [FireRedTeam/StoryMaker](https://github.com/FireRedTeam/StoryMaker) | 维持人物脸部、发型、服装跨帧/跨提示词的一致。 |
| **视频连贯性** | **ConsistI2V** | [TIGER-AI-Lab/ConsistI2V](https://github.com/TIGER-AI-Lab/ConsistI2V) | Image-to-Video 一致性，保持布局与运动连贯。 |
| **语音音色克隆**| **Amphion**, **Bark** | [open-mmlab/Amphion](https://github.com/open-mmlab/Amphion) | 高保真零样本声模仿，确保小说配音音色统一。 |

---

## 🏢 9. 分布式训练与参数一致性 (Distributed Training)
确保大规模模型在多 GPU/多节点训练过程中参数与梯度的绝对同步。

| 工具/算法 | 类型 | 关键特性 |
| :--- | :--- | :--- |
| **Megatron-LM** | 框架 | NVIDIA 出品，提供极致的模型并行 (TP/PP) 效率。 |
| **DeepSpeed** | 优化器/框架 | Microsoft ZeRO 技术，显存分片与大规模训练的标配。 |
| **FSDP** | 原生并行 | PyTorch 内置，全分片数据并行，ZeRO-3 的高性能替代。 |

---

## 🤝 10. 多代理协同与流程同步 (Multi-Agent Coordination)
在 Agent 团队协作过程中，确保共享状态、任务进度及上下文记忆的一致性。

| 项目名称 | 协调机制 | 特点 |
| :--- | :--- | :--- |
| **DeMAC** | 去中心化 | 消除 Zeno 效应，适合 1:1 动态响应的多代理系统。 |
| **Agentic-Sync** | 实时状态 | 支持开发者与 AI 协同，进度可视化同步。 |
| **Nexus Agents** | Redis 通信 | 基于 Redis 的 A2A 通信，实时跟踪多代理研究进度。 |

---

## 🏔️ 11. 在线训练与鲁棒对齐 (Online Training)
防止模型在与用户实时互动或在线微调（RLHF）过程中出现质量雪崩与价值观漂移。

| 名称 | GitHub 网址 | 核心特性 |
| :--- | :--- | :--- |
| **OpenRLHF** | [OpenRLHF/OpenRLHF](https://github.com/OpenRLHF/OpenRLHF) | 分布式 PPO/GRPO，包含严谨的 KL 散度约束防止对齐崩溃。 |
| **Online-RLHF** | [RLHFlow/Online-RLHF](https://github.com/RLHFlow/Online-RLHF) | 专注于在线迭代反馈，复现 LLaMA3 级模型的高稳定性。 |
| **RA-LLM** | [search/RA-LLM](https://github.com/search?q=RA-LLM+alignment) | 鲁棒对齐技术，显著降低对抗攻击下的 ASR 攻击成功率。 |

---

## 🌀 12. 持续学习与终身适应 (Continual Learning)
确保 LLM 在适应新场景、新领域时，不会产生灾难性遗忘，维持长期记忆的连续性。

| 名称 | GitHub 网址 | 算法背景 |
| :--- | :--- | :--- |
| **ContinualLM** | [UIC-Liu-Lab/ContinualLM](https://github.com/UIC-Liu-Lab/ContinualLM) | 领域自适应持续预训练框架，支持大规模增量学习。 |
| **CURLoRA** | [MNoorFawi/curlora](https://github.com/MNoorFawi/curlora) | 结合 CUR 分解的 LoRA 持续微调，兼具低开销与高稳定性。 |
| **Awesome Lifelong**| [zzz47zzz/awesome-lifelong-learning](https://github.com/zzz47zzz/awesome-lifelong-learning-methods-for-llm) | 汇总了包括 EWC、回放缓冲在内的所有主流防遗忘方案。 |

---

## 📚 外部资源
* [Awesome-RLHF](https://github.com/opendilab/awesome-RLHF) - RLHF 强化学习对齐全资源
* [Awesome LLM Pre-training](https://github.com/RUCAIBox/awesome-llm-pretraining) - 预训练策略与架构改进
* [Awesome-Audio-LLM](https://github.com/AudioLLMs/Awesome-Audio-LLM) - 音频大模型研究列表
* [ConsistI2V Projects](https://github.com/TIGER-AI-Lab/ConsistI2V) - 视频生成一致性研究
* [Awesome-Story-Generation](https://github.com/yingpengma/Awesome-Story-Generation) - 故事生成论文与算法集
* [GitHubDaily - 开源项目精选](https://github.com/GitHubDaily/GitHubDaily)

---

## 🤝 贡献
欢迎提交 PR 补充新的优质项目！请确保提供的 GitHub 链接真实有效。
