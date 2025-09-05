# awesome-ai-memory - A list of AI memory projects

| 名称                           | 网址                                      | 类型               | GitHub 网址                                   | 分类            | 存储类型       |
|--------------------------------|------------------------------------------|--------------------|----------------------------------------------|-----------------|----------------|
| Mem0 (mem zero)    | https://mem0.ai/                            | 托管，开源     | https://github.com/mem0ai/mem0                      | 内存工具     | 图形，向量     |
| Cognee             | https://www.cognee.ai/                       | 托管，开源     | https://github.com/topoteretes/cognee               | 内存工具     | 图形，向量     |
| Zep AI             | https://www.getzep.com/                      | 托管，开源     | https://github.com/getzep/zep                        | 内存工具     | 图形，向量     |
| Basic Memory       | https://github.com/Obsidian-BasicMemory    | 本地优先，开源 | https://github.com/Obsidian-BasicMemory              | 本地存储     | Markdown 文件  |
| Memories.ai        | https://memories.ai/                         | 托管，开源     | https://github.com/memories-ai/memories             | 记忆增强工具 | 视频+向量存储  |
| Chroma             | https://www.trychroma.com/                    | 开源           | https://github.com/chroma-core/chroma               | 向量数据库   | 向量+元数据   |
| Milvus             | https://milvus.io/                           | 开源           | https://github.com/milvus-io/milvus                  | 向量数据库   | 向量+元数据   |
| Qdrant             | https://qdrant.tech/                         | 开源           | https://github.com/qdrant/qdrant                      | 向量数据库   | 向量+元数据   |
| Memary             | https://finetune.dev/                    | 开源               | https://github.com/kingjulio8238/Memary       | 内存工具        | 图形           |
| Letta (MemGPT)     | https://memgpt.ai/                       | 托管，开源         | https://github.com/cpacker/MemGPT              | 内存工具        | 图形，向量     |
| GraphRAG (微软)     | https://microsoft.github.io/graphrag/   | 开源               | https://github.com/microsoft/graphrag          | 内存工具        | 图形，向量     |
| Llama Index        | https://www.llamaindex.ai/               | 托管，开源         | https://github.com/run-llama/llama_index       | LLM 框架        | 图形，向量     |
| LangChain          | https://www.langchain.com/               | 开源               | https://github.com/langchain-ai/langchain      | LLM 框架        | 向量           |
| Haystack           | https://haystack.deepset.ai/             | 开源               | https://github.com/deepset-ai                   | LLM 框架        | 向量           |
| Neo4j              | https://neo4j.com/                       | 托管，开源         | https://github.com/neo4j                        | 存储工具        | 图形           |
| Weaviate           | https://weaviate.io/                     | 开源               | https://github.com/weaviate/weaviate            | 存储工具        | 向量           |
| Faiss              | https://faiss.ai/                        | 开源               | https://github.com/facebookresearch/faiss       | 存储工具        | 向量           |
| OpenMemory MCP     | https://github.com/mem0ai/mem0/tree/main/openmemory | 开源    | https://github.com/mem0ai/mem0                   | 记忆共享协议    | 向量           |
| AutoGPT            | https://github.com/Significant-Gravitas/AutoGPT | 开源        | https://github.com/Significant-Gravitas/AutoGPT | AI Agent 框架   | 向量           |


结合最新的开源信息，以下是对现有awesome-ai-memory列表的优化和更新建议，包含了一些2025年最新值得关注的开源AI记忆方案及其分类、存储类型等内容：


# 更新和补充说明

- 新增了Basic Memory项目（本地优先，基于Markdown文件存储），支持无云端依赖，实现用户和AI间全双向长时记忆，适合注重隐私和本地化使用场景。
- 新增Memories.ai，专注于视频记忆的结构化存储和检索，结合向量数据库技术推动视频AI记忆能力。[2]
- 补充了Chroma、Milvus、Qdrant等领先开源向量数据库，它们被广泛用于存储和检索AI记忆的向量数据，具备高性能、扩展性和丰富的索引能力，成为AI记忆系统的底层存储主流方案。
- 现有项目Cognee、Zep AI、Mem0依然活跃且受关注，保持在列表中。
- 这些项目涵盖从内存工具、记忆引擎到向量数据库各种维度，支持多样化存储需求（图形、向量、多媒体、本地Markdown等）。

# 建议

- 根据具体应用场景选择合适的存储类型，例如需要隐私保护可选Basic Memory的本地存储，云端智能代理则选择Mem0或Zep AI等。
- 对于大规模、低延迟检索需求，结合Milvus、Chroma等开源向量数据库作为底层存储方案。
- 关注项目的社区活跃度和技术更新，确保持续支持和版本迭代。

此优化后的内容既包含目前主流的AI内存工具，也涵盖了底层存储新兴的开源矢量数据库方案，符合2025年最新技术趋势和应用需求。欢迎根据应用场景进一步定制选择和集成。

------

### 说明：

- **Mem0** 是目前最具代表性的AI记忆层工具，支持多层次记忆、自适应个性化，解决大模型“记忆断片”问题，具备高效记忆检索和智能记忆更新机制，适合长期记忆和上下文连贯性需求。
- **Cognee、Zep AI、Memary、Letta (MemGPT)、GraphRAG** 等项目均结合知识图谱和向量存储，支持动态语义记忆和高级推理，适合构建有状态AI智能体。
- **Llama Index、LangChain、Haystack** 是当前主流的LLM框架，提供强大的向量检索和记忆管理能力，广泛应用于AI智能体和RAG系统。
- **Neo4j、Weaviate、Milvus、Qdrant、Faiss** 是行业领先的图数据库和向量数据库，支撑高效存储与检索，适合大规模知识和记忆管理。
- **OpenMemory MCP** 是最新发布的本地存储与跨工具记忆共享协议，支持多客户端无缝同步，提升多工具协作效率，适合注重隐私和本地化的场景。
- **AutoGPT** 作为热门AI Agent项目，具备高度自主性和模块化设计，集成内存管理，支持复杂任务自动执行，适合开发者学习和应用。

以上项目和工具均为2024-2025年持续活跃、社区认可度高、技术前沿且实用的AI记忆及智能体相关资源，适合用于构建和优化具备长期记忆和上下文理解能力的AI系统。

