# Awesome AI Memory - 大语言模型长期记忆项目精选列表

这是一个专注于大语言模型（LLM）长期记忆（Long-term Memory）实现的精选列表，覆盖从底层检索/存储范式、记忆层系统、Agent 记忆工具，到多模态一致性、训练与对齐的完整生态。

## 核心更新（2025-2026）

- **Mem0g 图谱版落地**：Mem0 在向量记忆之外推出图谱版 Mem0g，强化实体关系推理与跨会话记忆整合。
- **叙事增强**：针对长篇写作与叙事连贯性的专项记忆算法与工具逐渐成熟，覆盖人物弧线、情节线与情感弧跟踪。
- **MCP 生态扩张**：涌现大量支持 Cursor、Claude Desktop、OpenClaw 等宿主的本地优先记忆插件，记忆能力正从"云端托管"走向"本地可私有化"。
- **架构层记忆**：Titans 等神经长期记忆模块让"记忆"从外部检索进一步下探到模型架构与测试时学习。

---

## 大模型记忆技术演进

理解下面各项目的定位，需要先把记忆技术的发展脉络理清。以下按时间顺序列出经过验证的关键里程碑（年份/机构以原始论文为准）。

### 范式奠基

- **RAG（检索增强生成，Meta/FAIR，2020，arXiv 2005.11401）**：检索 + 生成范式，被视为 LLM 参数外记忆的基础。把"知识"放在外部语料里，按需检索注入上下文。
- **Generative Agents（斯坦福，Park 等，2023，arXiv 2304.03442）**：25 个 AI agent 组成的小镇，提出"记忆流（memory stream）+ 检索 + 反思（reflection）"三件套，是 Agent 记忆设计的经典原型。

### 记忆机制探索（2023）

- **MemoryBank（Zhong 等，2023，arXiv 2305.10250，AAAI 2024）**：受艾宾浩斯遗忘曲线启发，对记忆做衰减与强化，配套 LoCoMo 长程对话记忆评测集。
- **LongMem（Wang 等，2023，arXiv 2306.07174，NeurIPS 2023）**：冻结主干 LLM 作记忆编码器，配合 Residual SideNet 与缓存记忆库，实现长时记忆。
- **MemGPT / Letta（UC Berkeley，Packer 等，2023，arXiv 2310.08560）**：把操作系统虚拟内存思想用于 LLM，将上下文分层为主上下文/外部存储，用工具调用做"虚拟上下文管理"。团队后续成立 Letta 公司延续开源项目。

### 记忆压缩与情景记忆（2024）

- **ReadAgent（Google DeepMind，2024）**：模拟人类阅读，将长文分页（pagination）并用 gist memory 压缩要点，属于情景式记忆框架。
- **GraphRAG（Microsoft，2024，arXiv 2404.16130）**：从非结构化文本抽取实体关系构建知识图谱，并对社区做摘要，提升复杂/全局问答的检索增强。
- **HippoRAG（OSU-NLP-Group 与 Stanford 等，2024，arXiv 2405.14831，NeurIPS 2024）**：受海马体索引理论启发，协同 LLM、知识图谱与个性化 PageRank 实现类长期记忆的多跳检索。
- **Memory3 / 显性记忆（BAAI 智源研究院等，2024，arXiv 2407.01178）**：把知识外挂为稀疏注意力 KV 记忆模块，与参数记忆、工作记忆并列成为"第三种记忆"。

### 生产级记忆层（2025）

- **Mem0（Mem0 团队，2025，arXiv 2504.19413）**：面向生产级 AI agent 的可扩展长期记忆层，含向量版 Mem0 与图谱版 Mem0g，论文称在 LLM-as-Judge 评测上优于 OpenAI 记忆方案且更省 token。
- **A-MEM（Xu 等，2025，arXiv 2502.12110）**：受卢曼 Zettelkasten 卡片盒笔记法启发，以动态索引/链接实现 agent 自主演化的结构化记忆，与 Zep/Graphiti 路线同类但独立。

### 架构层长期记忆（2024-2025）

- **Titans（Google，2024-12，arXiv 2412.01427，NeurIPS 2025）**：提出"神经长期记忆（neural long-term memory）"模块，以"惊奇度"驱动、支持 test-time training/learning，将 RNN 式记忆与注意力结合处理超长上下文。

> 演进主线：外部检索（RAG）→ Agent 记忆流与反思（Generative Agents / MemGPT）→ 记忆压缩与图谱化（ReadAgent / GraphRAG / HippoRAG / Memory3）→ 生产级记忆层（Mem0 / A-MEM / Zep）→ 架构内神经长期记忆（Titans）。记忆正从"提示词里塞资料"走向"模型自身学会记住"。

---

## 1. 聚合记忆层（Integrated Memory Layers）

这类项目提供逻辑复杂的记忆管理，支持多用户、多会话、自动摘要与知识提取。

| 名称 | GitHub 网址 | 类型 | 存储类型 | 特点 |
| :--- | :--- | :--- | :--- | :--- |
| **Mem0** | [mem0ai/mem0](https://github.com/mem0ai/mem0) | 托管/开源 | 图形 + 向量 | 智能记忆层，含向量版 Mem0 与图谱版 Mem0g，支持跨用户/会话记忆。 |
| **Memobase** | [memodb-io/memobase](https://github.com/memodb-io/memobase) | 开源 | Profile-based | 专注于事件演化与人物画像的长期记忆管理。 |
| **Graphiti** | [getzep/graphiti](https://github.com/getzep/graphiti) | 开源 | 时序知识图谱 | Zep Core 开源版，专注随时间演变的动态关联知识存储。 |
| **LangMem** | [langchain-ai/langmem](https://github.com/langchain-ai/langmem) | 开源 | 向量 + 属性 | LangChain 官方长期记忆，自动提取、整合并更新知识。 |
| **Zep AI** | [getzep/zep](https://github.com/getzep/zep) | 托管/开源 | 图形 + 向量 | 聊天记忆平台，提供情感分析与深度总结功能。 |
| **Letta** | [letta-ai/letta](https://github.com/letta-ai/letta) | 托管/开源 | 分层存储 | 原 MemGPT，将记忆视为操作系统的多级缓存（RAM/Disk）。 |
| **SimpleMem** | [aiming-lab/SimpleMem](https://github.com/aiming-lab/SimpleMem) | 开源 | 多模态 | 终身记忆层，支持跨对话的项目历史记忆，含多模态能力。 |

---

## 2. Agent 与本地记忆工具（Agentic & Local Tools）

适合个人开发者、单机 Agent 或集成到特定办公流程的项目。

| 名称 | GitHub 网址 | 类型 | 特点 |
| :--- | :--- | :--- | :--- |
| **NovelGenerator** | [KazKozDev/NovelGenerator](https://github.com/KazKozDev/NovelGenerator) | 多代理 | 跟踪人物视角、情节线与情感弧，适合生成完整小说。 |
| **AgentCortex** | [sage-hq/agentcortex-mcp](https://github.com/sage-hq/agentcortex-mcp) | MCP | 原生 MCP 记忆系统，支持 Cursor 和 Claude Desktop。 |
| **Basic Memory** | [basicmachines-co/basic-memory](https://github.com/basicmachines-co/basic-memory) | MCP/SQLite | 基于 SQLite 与 Markdown，极其隐私友好，适合本地知识库。 |
| **Lians** | [Lians-ai/Lians](https://github.com/Lians-ai/Lians) | MCP/SQLite | 开源、本地优先的 AI Agent 记忆层，支持跨会话持久召回；提供 MCP、SDK 与桌面安装程序，无需账号或 API 密钥。 |
| **Nano-GraphRAG** | [gusye1234/nano-graphrag](https://github.com/gusye1234/nano-graphrag) | 本地优化 | 极轻量级 GraphRAG 实现，适合资源受限环境。 |
| **SimpleMem** | [aiming-lab/SimpleMem](https://github.com/aiming-lab/SimpleMem) | 开源 | 终身记忆层，支持跨对话的项目历史记忆。 |
| **Supermemory** | [supermemoryai/supermemory](https://github.com/supermemoryai/supermemory) | 云原生 | 基于 Cloudflare 生态，构建分布式的个人 AI 记忆大脑。 |
| **Khoj** | [khoj-ai/khoj](https://github.com/khoj-ai/khoj) | 多端 | 个人 AI 副驾驶，深度集成 Markdown 文档与笔记。 |

---

## 3. 框架集成（AI Frameworks with Memory Support）

深度集成了长期记忆管理能力的通用 AI 开发框架。

| 名称 | GitHub 网址 | 核心能力 |
| :--- | :--- | :--- |
| **LlamaIndex** | [run-llama/llama_index](https://github.com/run-llama/llama_index) | 提供 Property Graph Index 和多种叙事增强的索引模式。 |
| **LangChain** | [langchain-ai/langchain](https://github.com/langchain-ai/langchain) | 内置多种 Memory 组件，支持与各类向量库无缝对接。 |

---

## 4. 基础设施与存储（Infrastructure & Storage）

为上述记忆层提供物理支撑的基础数据库。

| 分类 | 推荐项目 | 核心能力 |
| :--- | :--- | :--- |
| **向量数据库** | [Chroma](https://github.com/chroma-core/chroma), [Milvus](https://github.com/milvus-io/milvus), [Qdrant](https://github.com/qdrant/qdrant), [Weaviate](https://github.com/weaviate/weaviate) | 高效的语义相似度搜索与混合检索。 |
| **图数据库** | [Neo4j](https://github.com/neo4j) | 复杂的实体关系推理与深度关联分析。 |

---

## 5. 选型与集成建议（Practical Integration）

1. **从小处着手**：建议初学者从**向量数据库**开始。除非业务需要（如复杂的情节线推理），否则避免过早引入复杂的图谱结构。
2. **长篇叙事（Storytelling）**：
   - 优先使用 **Mem0** 或 **NovelGenerator** 跟踪人物弧线。
   - **策略建议**：先生成并存储章节摘要，在生成新章节前检索摘要以保证连贯性。
3. **生态兼容性**：
   - OpenClaw（原 Clawdbot）等个人助手用户，建议使用提供成熟 SDK 的 Mem0 或 Letta。
4. **隐私敏感**：本地 Agent 首选 **Basic Memory** 或 **AgentCortex**。

---

## 6. 预训练与架构增强（Research & Architecture）

专注于在训练阶段或架构层面提升 LLM 记忆能力的先进研究。

| 名称 | GitHub 网址 | 焦点内容 |
| :--- | :--- | :--- |
| **Titans** | [google-research/titans](https://github.com/google-research/titans) | Google 提出的经由神经记忆模块提升长文本处理的架构。 |
| **HOMER** | [alinlab/HOMER](https://github.com/alinlab/HOMER) | 层次上下文合并（ICLR 2024），高效扩展上下文长度。 |
| **Memory3** | [BAAI-Agents/Memory3](https://github.com/BAAI-Agents/Memory3) | BAAI 提出的显性记忆大模型，将知识外挂为稀疏记忆模块。 |
| **Awesome LLM Pre-training** | [RUCAIBox/awesome-llm-pretraining](https://github.com/RUCAIBox/awesome-llm-pretraining) | 预训练策略、架构改进（如 Ultra-Sparse Memory）研究精选。 |

---

## 7. MCP 与技能插件（MCP & Assistant Skills）

利用模型上下文协议（MCP）或特定工具调用（Skills）为模型注入持久记忆的能力。

| 名称 | GitHub 网址 | 类型 | 特点 |
| :--- | :--- | :--- | :--- |
| **memento-mcp** | [gannonh/memento-mcp](https://github.com/gannonh/memento-mcp) | MCP | 知识图谱驱动的记忆系统，支持语义检索与时间感知。 |
| **OpenClaw Skills** | [VoltAgent/awesome-openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills) | Skills | 包含 Git-notes 记忆、LanceDB 三重记忆等 OpenClaw 专属技能。 |
| **mcp-memory** | [samwang0723/mcp-memory](https://github.com/samwang0723/mcp-memory) | MCP/Redis | 使用 Redis Graph 作为后端的知识图谱 MCP 服务器。 |

---

## 8. 多模态一致性与记忆（Multimodal Consistency & Memory）

在生成图像和视频时维持角色形象、画风及音色一致性的专用工具与算法。

| 分类 | 推荐项目 | GitHub 网址 | 核心特性 |
| :--- | :--- | :--- | :--- |
| **视觉一致性** | **StoryMaker**, **IP-Adapter** | [FireRedTeam/StoryMaker](https://github.com/FireRedTeam/StoryMaker) | 维持人物脸部、发型、服装跨帧/跨提示词的一致。 |
| **视频连贯性** | **ConsistI2V** | [TIGER-AI-Lab/ConsistI2V](https://github.com/TIGER-AI-Lab/ConsistI2V) | Image-to-Video 一致性，保持布局与运动连贯。 |
| **语音音色克隆** | **Amphion**, **Bark** | [open-mmlab/Amphion](https://github.com/open-mmlab/Amphion) | 高保真零样本声模仿，确保小说配音音色统一。 |

---

## 9. 分布式训练与参数一致性（Distributed Training）

确保大规模模型在多 GPU/多节点训练过程中参数与梯度的绝对同步。

| 工具/算法 | 类型 | 关键特性 |
| :--- | :--- | :--- |
| **Megatron-LM** | 框架 | NVIDIA 出品，提供极致的模型并行（TP/PP）效率。 |
| **DeepSpeed** | 优化器/框架 | Microsoft ZeRO 技术，显存分片与大规模训练的标配。 |
| **FSDP** | 原生并行 | PyTorch 内置，全分片数据并行，ZeRO-3 的高性能替代。 |

---

## 10. 多代理协同与流程同步（Multi-Agent Coordination）

在 Agent 团队协作过程中，确保共享状态、任务进度及上下文记忆的一致性。

| 项目名称 | 协调机制 | 特点 |
| :--- | :--- | :--- |
| **DeMAC** | 去中心化 | 消除 Zeno 效应，适合 1:1 动态响应的多代理系统。 |
| **Nexus Agents** | Redis 通信 | 基于 Redis 的 A2A 通信，实时跟踪多代理研究进度。 |

---

## 11. 在线训练与鲁棒对齐（Online Training）

防止模型在与用户实时互动或在线微调（RLHF）过程中出现质量雪崩与价值观漂移。

| 名称 | GitHub 网址 | 核心特性 |
| :--- | :--- | :--- |
| **OpenRLHF** | [OpenRLHF/OpenRLHF](https://github.com/OpenRLHF/OpenRLHF) | 分布式 PPO/GRPO，包含严谨的 KL 散度约束防止对齐崩溃。 |
| **Online-RLHF** | [RLHFlow/Online-RLHF](https://github.com/RLHFlow/Online-RLHF) | 专注于在线迭代反馈，复现 LLaMA3 级模型的高稳定性。 |

---

## 12. 持续学习与终身适应（Continual Learning）

确保 LLM 在适应新场景、新领域时，不会产生灾难性遗忘，维持长期记忆的连续性。

| 名称 | GitHub 网址 | 算法背景 |
| :--- | :--- | :--- |
| **ContinualLM** | [UIC-Liu-Lab/ContinualLM](https://github.com/UIC-Liu-Lab/ContinualLM) | 领域自适应持续预训练框架，支持大规模增量学习。 |
| **CURLoRA** | [MNoorFawi/curlora](https://github.com/MNoorFawi/curlora) | 结合 CUR 分解的 LoRA 持续微调，兼具低开销与高稳定性。 |
| **Awesome Lifelong** | [zzz47zzz/awesome-lifelong-learning](https://github.com/zzz47zzz/awesome-lifelong-learning-methods-for-llm) | 汇总了包括 EWC、回放缓冲在内的所有主流防遗忘方案。 |

---

## 13. 记忆技术演进鱼骨图

下面用鱼骨图（因果骨架图）梳理"大模型记忆能力从何而来"的几条主线，便于快速建立全局认知。鱼头是"LLM 长期记忆能力"，骨架上的每条"大骨"是一个技术维度，分支是代表性工作。

```
                                          ┌─ RAG (2020, Meta) ................ 参数外记忆基础
                                          ├─ GraphRAG (2024, MS) ........... 图谱 + 社区摘要
                      检索/外部记忆 ──────┼─ HippoRAG (2024) ............... 海马体索引 + PPR
                                          └─ Memory3 (2024, BAAI) .......... 显性/稀疏记忆模块
                                                 │
                                                 ├─ Generative Agents (2023) . 记忆流 + 反思
                                                 ├─ MemGPT / Letta (2023) .... 虚拟上下文分层
                      机制/架构记忆 ─────────────┼─ LongMem (2023) ............ 冻结编码 + 缓存库
                                                 ├─ ReadAgent (2024) ......... 分页 + gist 压缩
                                                 └─ Titans (2024-25, Google) . 神经长期记忆 + 测试时学习
                                                 │
                                                 ├─ MemoryBank (2023) ........ 遗忘曲线衰减
                      生产级记忆层 ──────────────┼─ Mem0 / Mem0g (2025) ...... 向量 + 图谱记忆层
                                                 ├─ Zep / Graphiti ........... 时序知识图谱
                                                 └─ A-MEM (2025) ............. Zettelkasten 自主演化
                                                 │
                      工具/协议生态 ──────────────┼─ MCP: AgentCortex / memento-mcp
                                                 ├─ 本地优先: Basic Memory
                                                 └─ 技能: OpenClaw Skills
                                                 │
                                                 ├─ 多模态: StoryMaker / ConsistI2V / Amphion
                      垂直场景延展 ──────────────┼─ 叙事: NovelGenerator
                                                 └─ 多代理: DeMAC / Nexus Agents
                                                 │
   LLM 长期记忆能力  ◄───────────────────────────┘
   (鱼头)
```

阅读方法：从左上"检索/外部记忆"到右下"垂直场景延展"，技术由"通用范式"逐步下沉到"架构内记忆"并扩散到具体场景。每条大骨彼此并非互斥——例如 Mem0 同时用到检索与图谱，Titans 把记忆写进架构。

---

## 外部资源

- [Awesome-RLHF](https://github.com/opendilab/awesome-RLHF) - RLHF 强化学习对齐全资源
- [Awesome LLM Pre-training](https://github.com/RUCAIBox/awesome-llm-pretraining) - 预训练策略与架构改进
- [Awesome-Audio-LLM](https://github.com/AudioLLMs/Awesome-Audio-LLM) - 音频大模型研究列表
- [ConsistI2V Projects](https://github.com/TIGER-AI-Lab/ConsistI2V) - 视频生成一致性研究
- [Awesome-Story-Generation](https://github.com/yingpengma/Awesome-Story-Generation) - 故事生成论文与算法集
- [GitHubDaily - 开源项目精选](https://github.com/GitHubDaily/GitHubDaily)

---

## 贡献

欢迎提交 PR 补充新的优质项目！请确保提供的 GitHub 链接真实有效、描述与官方定位一致。
