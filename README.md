# Awesome AI Memory - 大语言模型长期记忆项目精选列表

这是一个专注于大语言模型（LLM）长期记忆（Long-term Memory）实现的精选列表，覆盖从底层检索/存储范式、记忆层系统、Agent 记忆工具，到多模态一致性、训练与对齐的完整生态。

## 核心更新（2026 Q2–Q3）

- **记忆管理 RL 化**：AgeMem 等把长期/短期记忆的增删改查变成 agent 可训练的工具动作，用三阶段 RL（step-wise GRPO）端到端优化，取代启发式控制器。
- **从"原子事实"到多粒度**：TriMem 同时保留原始对话片段、抽取事实与合成画像三层粒度，用 TextGrad 迭代优化提示词，实现无参数更新的终身演化。
- **冲突感知与事实修订**：MOSAIC、Infini Memory 针对"事实随时间变化"设计可维护记忆（主题文档 / 冲突检测），直击写路径质量控制难题。
- **评测从"召回"转向"行动"**：MemoryAgentBench（ICLR'26）、MemoryArena / Memoria-Bench / AMA-Bench（ICML'26）、HaluMem、LongMemEval-V2 把评估推向操作级幻觉、多会话 agentic 任务与选择性遗忘。
- **测试时记忆层化**：Titans-as-a-Layer 把神经长期记忆做成即插即用适配器（MAL），无需改动主干即可为多模态模型注入长期记忆。
- **本地优先跨工具 MCP 记忆**：Memorix、OKF 标准的 mcp-memory 等以 SQLite / 知识图谱 + Markdown 落地，强调私有化与跨宿主（Claude Code / Cursor / Codex）共享。

---

## 近期重要进展（2026 年 6–9 月）

### 新论文与新方法

| 名称 | 来源 | 核心贡献 |
| :--- | :--- | :--- |
| **AgeMem（Agentic Memory）** | [arXiv 2601.01885](https://arxiv.org/abs/2601.01885) · ACL 2026 SAC Highlight | 把 LTM/STM 的存储、检索、更新、摘要、丢弃统一为 agent 工具动作，三阶段渐进式 RL + step-wise GRPO 训练，消除启发式控制器。 |
| **TriMem** | [arXiv 2605.19952](https://arxiv.org/abs/2605.19952) | 突破"抽取原子事实"范式，同时维护原始对话、原子事实、合成画像三种粒度；TextGrad 迭代优化抽取/画像提示，无参数终身演化。 |
| **Infini Memory** | [arXiv 2606.10677](https://arxiv.org/abs/2606.10677) | 把记忆组织成可维护的"主题文档"，新观测先入缓冲再周期合并；推理时用迭代式工具调用读取记忆，MemoryAgentBench 达 64.7%。 |
| **MOSAIC** | [arXiv 2607.16211](https://arxiv.org/abs/2607.16211) | 冲突感知的结构化长期记忆，显式检测事实冲突（命中 66% vs 基线 14%），LoCoMo 准确率 89.35%。 |
| **H-MEM** | [EACL 2026](https://aclanthology.org/2026.eacl-long.15.pdf) | 四层层次化记忆（领域→子域→关键词→事件/画像），前三层作为可解释索引提升长程推理效率。 |
| **Titans-as-a-Layer（MAL）** | [arXiv 2606.08573](https://arxiv.org/abs/2606.08573) | 把 Titans 式测试时神经记忆做成即插即用的 Memory-as-a-Layer 适配器，为音频大模型注入对话历史而不改主干。 |
| **MemDelta** | [arXiv 2606.29914](https://arxiv.org/abs/2606.29914) | 指出 agent 记忆评测中的隐藏混淆变量并给出受控基线，质疑此前评测结论的可比性。 |
| **Diagnosing Retrieval vs. Utilization** | [arXiv 2603.02473](https://arxiv.org/abs/2603.02473) | 实证发现：检索质量对最终效果的影响远大于写入/压缩策略，原始分块即可媲美复杂事实抽取。 |
| **How Memory Management Impacts LLM Agents** | [ACL 2026](https://aclanthology.org/2026.acl-long.27.pdf) | 系统研究"经验跟随"行为，揭示错误传播与错位经验回放，提出基于历史的记忆删除策略。 |

### 新数据集与基准

完整清单见 [`docs/memory-evaluation-benchmarks.md`](docs/memory-evaluation-benchmarks.md)。

| 基准 | 来源 | 评测重点 |
| :--- | :--- | :--- |
| **MemoryAgentBench** | ICLR 2026 · [GitHub](https://github.com/HUST-AI-HYZ/MemoryAgentBench) | 四维能力：精确检索、测试时学习、长程理解、选择性遗忘；新增 EventQA 与 FactConsolidation。 |
| **MemoryArena** | ICML 2026 · [GitHub](https://github.com/ZexueHe/MemoryArena) | 多会话 Memory-Agent-Environment 闭环，子任务相互依赖（网页导航/偏好规划/渐进搜索/形式推理）。 |
| **Memoria-Bench** | ICML 2026 · [论文](https://palm.seu.edu.cn/zhangml/files/ICML%2726a.pdf) | 长程自主 agent 的情景/语义/程序记忆，覆盖深度研究、代码、表格任务；揭示百万 token 上下文仍存在的记忆瓶颈。 |
| **AMA-Bench** | ICML 2026 · [GitHub](https://github.com/AMA-Bench/AMA-Bench) | 长程 agent 轨迹（状态/动作/观测/工具输出）的长上下文保留与长时程记忆表现。 |
| **HaluMem** | [arXiv 2511.03506](https://arxiv.org/abs/2511.03506) | 首个操作级记忆幻觉基准，拆解抽取 / 更新 / 问答三阶段。 |
| **LongMemEval-V2** | [arXiv 2605.12493](https://arxiv.org/abs/2605.12493) | 面向 web agent 环境经验（静态/动态状态、工作流、坑点、前提感知），历史轨迹最长 115M tokens。 |
| **Mem-Gallery** | [ACL 2026](https://aclanthology.org/2026.acl-long.1892/) | 多模态长程对话记忆，评测 MLLM agent 的抽取/测试时适应、推理与知识管理。 |
| **Mem2ActBench** | [ACL 2026](https://aclanthology.org/2026.acl-long.370/) | 评测 agent 能否主动用长期记忆驱动工具选择与参数落地（非被动问答）。 |
| **EverMemBench** | [arXiv 2602.01313](https://arxiv.org/abs/2602.01313) | 多方职场对话，细粒度召回 / 记忆意识 / 用户画像理解。 |
| **Memora** | [ACL 2026](https://github.com/geniesinc/Memora) · [arXiv 2604.20006](https://arxiv.org/abs/2604.20006) | 面向个性化 agent，同时给"该记住"与"该忘记（已删除/更新）"打分，提出 FAMA 指标。 |
| **MemoryBench** | [arXiv 2510.17281](https://arxiv.org/abs/2510.17281) | 记忆 + 持续学习，on-policy / off-policy 交互模拟。 |
| **BEAM** | ICLR 2026 | 百万 token 级长期记忆的召回与增强。 |

### 新趋势

1. **记忆管理 RL 化**：记忆操作不再是固定流水线，而是策略的一部分，由奖励信号驱动"该记什么、何时忘"。
2. **多粒度 + 冲突感知的写路径**：从"抽取原子事实"转向同时保留原文、事实与画像，并显式处理事实冲突与修订。
3. **评测操作级 / agentic 化**：评估从端到端 QA 分数，细化为抽取、更新、遗忘等环节，并转向多会话、可行动的任务。
4. **测试时记忆层化**：神经长期记忆从"改架构"变为"可插拔层"，降低多模态模型注入长期记忆的门槛。
5. **本地优先与标准化**：MCP 记忆服务强调本地运行、跨宿主共享，并出现 OKF 等记忆文件格式标准。
6. **从"能记住"到"能行动"**：Mem2ActBench、MemoryArena 等直接检验记忆对工具调用与决策的增益。

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

### 记忆管理学习化与评测体系（2026）

- **AgeMem / Agentic Memory（2026，arXiv 2601.01885，ACL 2026）**：把 LTM/STM 操作作为工具动作交给 agent 自主决策，用渐进式 RL 训练，标志记忆管理从启发式规则走向可学习策略。
- **TriMem（2026，arXiv 2605.19952）**：以"原始对话 + 原子事实 + 合成画像"三种粒度共存替代单一事实抽取，配合 TextGrad 提示优化实现无参数终身演化。
- **Infini Memory（2026，arXiv 2606.10677）**：把记忆重构为可维护的"主题文档"，配合迭代式 agentic 检索，强调证据聚合与事实修订。
- **Titans-as-a-Layer（2026，arXiv 2606.08573）**：将测试时神经记忆封装为可插拔层（MAL），从"改架构"转向"加模块"，首次系统扩展到音频多模态。
- **评测体系（2026）**：MemoryAgentBench（ICLR）、MemoryArena / Memoria-Bench / AMA-Bench（ICML）、HaluMem、LongMemEval-V2 等把评测细化到抽取/更新/遗忘等操作环节与多会话 agentic 任务。

> 演进主线：外部检索（RAG）→ Agent 记忆流与反思（Generative Agents / MemGPT）→ 记忆压缩与图谱化（ReadAgent / GraphRAG / HippoRAG / Memory3）→ 生产级记忆层（Mem0 / A-MEM / Zep）→ 架构内神经长期记忆（Titans）→ 可学习的记忆管理 + 操作级评测（AgeMem / TriMem / MemoryAgentBench）。记忆正从"提示词里塞资料"走向"模型自身学会记住、并学会管理该记什么"。

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
| **MemoryOS** | [BAI-LAB/MemoryOS](https://github.com/BAI-LAB/MemoryOS) | 开源 | 分层存储 | 借鉴操作系统内存分页思想的分层记忆管理（arXiv 2506.06326），常被作为记忆评测基线。 |

---

## 2. Agent 与本地记忆工具（Agentic & Local Tools）

适合个人开发者、单机 Agent 或集成到特定办公流程的项目。

| 名称 | GitHub 网址 | 类型 | 特点 |
| :--- | :--- | :--- | :--- |
| **NovelGenerator** | [KazKozDev/NovelGenerator](https://github.com/KazKozDev/NovelGenerator) | 多代理 | 跟踪人物视角、情节线与情感弧，适合生成完整小说。 |
| **AgentCortex** | [sage-hq/agentcortex-mcp](https://github.com/sage-hq/agentcortex-mcp) | MCP | 原生 MCP 记忆系统，支持 Cursor 和 Claude Desktop。 |
| **Basic Memory** | [basicmachines-co/basic-memory](https://github.com/basicmachines-co/basic-memory) | MCP/SQLite | 基于 SQLite 与 Markdown，极其隐私友好，适合本地知识库。 |
| **Nano-GraphRAG** | [gusye1234/nano-graphrag](https://github.com/gusye1234/nano-graphrag) | 本地优化 | 极轻量级 GraphRAG 实现，适合资源受限环境。 |
| **SimpleMem** | [aiming-lab/SimpleMem](https://github.com/aiming-lab/SimpleMem) | 开源 | 终身记忆层，支持跨对话的项目历史记忆。 |
| **Supermemory** | [supermemoryai/supermemory](https://github.com/supermemoryai/supermemory) | 云原生 | 基于 Cloudflare 生态，构建分布式的个人 AI 记忆大脑。 |
| **Khoj** | [khoj-ai/khoj](https://github.com/khoj-ai/khoj) | 多端 | 个人 AI 副驾驶，深度集成 Markdown 文档与笔记。 |

---
| **Hyperconsciousness** | [louis030195/hyperconsciousness](https://github.com/louis030195/hyperconsciousness) | Rust / MCP | 开发者 Alpha 阶段的加密、仅追加知识存储，通过有范围和有效期限制的授权提供 MCP 搜索与读取。 |

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
| **AgeMem** | [arXiv 2601.01885](https://arxiv.org/abs/2601.01885) | 用强化学习统一学习 LTM/STM 的存储、检索、更新与遗忘策略（ACL 2026）。 |
| **Titans-as-a-Layer** | [arXiv 2606.08573](https://arxiv.org/abs/2606.08573) | 即插即用的测试时记忆适配层（MAL），可扩展至音频多模态。 |
| **Awesome LLM Pre-training** | [RUCAIBox/awesome-llm-pretraining](https://github.com/RUCAIBox/awesome-llm-pretraining) | 预训练策略、架构改进（如 Ultra-Sparse Memory）研究精选。 |

---

## 7. MCP 与技能插件（MCP & Assistant Skills）

利用模型上下文协议（MCP）或特定工具调用（Skills）为模型注入持久记忆的能力。

| 名称 | GitHub 网址 | 类型 | 特点 |
| :--- | :--- | :--- | :--- |
| **memento-mcp** | [gannonh/memento-mcp](https://github.com/gannonh/memento-mcp) | MCP | 知识图谱驱动的记忆系统，支持语义检索与时间感知。 |
| **OpenClaw Skills** | [VoltAgent/awesome-openclaw-skills](https://github.com/VoltAgent/awesome-openclaw-skills) | Skills | 包含 Git-notes 记忆、LanceDB 三重记忆等 OpenClaw 专属技能。 |
| **mcp-memory** | [samwang0723/mcp-memory](https://github.com/samwang0723/mcp-memory) | MCP/Redis | 使用 Redis Graph 作为后端的知识图谱 MCP 服务器。 |
| **Memorix** | [avids2/memorix](https://github.com/avids2/memorix) | MCP | 本地优先的跨工具共享记忆层，支持 Claude Code / Codex / Cursor / OpenCode 等。 |
| **mcp-memory (OKF)** | [fellowgeek/mcp-memory](https://github.com/fellowgeek/mcp-memory) | MCP/SQLite | 基于 Open Knowledge Format v0.2 + SQLite FTS5 的持久记忆服务，Markdown 可读可审计。 |

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
                                                 ├─ Titans (2024-25, Google) . 神经长期记忆 + 测试时学习
                                                 └─ Titans-as-a-Layer (2026) . 记忆层化，即插即用
                                                 │
                                                 ├─ MemoryBank (2023) ........ 遗忘曲线衰减
                      生产级记忆层 ──────────────┼─ Mem0 / Mem0g (2025) ...... 向量 + 图谱记忆层
                                                 ├─ Zep / Graphiti ........... 时序知识图谱
                                                 └─ A-MEM (2025) ............. Zettelkasten 自主演化
                                                 │
                                                 ├─ AgeMem (2026) ............ RL 学习记忆管理策略
                      可学习记忆管理 (2026) ─────┼─ TriMem (2026) ............. 多粒度 + 无参数演化
                                                 ├─ Infini Memory (2026) ..... 主题文档 + 事实修订
                                                 └─ MOSAIC (2026) ............ 冲突感知结构化记忆
                                                 │
                                                 ├─ MemoryAgentBench (ICLR'26)  四维能力解耦
                      评测体系 (2026) ───────────┼─ MemoryArena / Memoria-Bench 多会话 agentic
                                                 ├─ HaluMem ................... 操作级幻觉
                                                 └─ LongMemEval-V2 ............ 环境经验记忆
                                                 │
                                                 ├─ MCP: AgentCortex / memento-mcp
                      工具/协议生态 ─────────────┼─ 本地优先: Basic Memory / Memorix / OKF
                                                 └─ 技能: OpenClaw Skills
                                                 │
                                                 ├─ 多模态: StoryMaker / ConsistI2V / Amphion
                      垂直场景延展 ──────────────┼─ 叙事: NovelGenerator
                                                 └─ 多代理: DeMAC / Nexus Agents
                                                 │
   LLM 长期记忆能力  ◄───────────────────────────┘
   (鱼头)
```

阅读方法：从左上"检索/外部记忆"到右下"垂直场景延展"，技术由"通用范式"逐步下沉到"架构内记忆"并扩散到具体场景。每条大骨彼此并非互斥——例如 Mem0 同时用到检索与图谱，Titans 把记忆写进架构，AgeMem 则把记忆管理本身交给策略学习。

---

## 外部资源

- [Awesome-RLHF](https://github.com/opendilab/awesome-RLHF) - RLHF 强化学习对齐全资源
- [Awesome LLM Pre-training](https://github.com/RUCAIBox/awesome-llm-pretraining) - 预训练策略与架构改进
- [Awesome-Audio-LLM](https://github.com/AudioLLMs/Awesome-Audio-LLM) - 音频大模型研究列表
- [ConsistI2V Projects](https://github.com/TIGER-AI-Lab/ConsistI2V) - 视频生成一致性研究
- [Awesome-Story-Generation](https://github.com/yingpengma/Awesome-Story-Generation) - 故事生成论文与算法集
- [awesome-agent-memory](https://github.com/Snseam/awesome-agent-memory) - Agent 长期记忆的结构化证据库（论文索引、产品与基准对比）
- [GitHubDaily - 开源项目精选](https://github.com/GitHubDaily/GitHubDaily)

---

## 贡献

欢迎提交 PR 补充新的优质项目！请确保提供的 GitHub 链接真实有效、描述与官方定位一致。
