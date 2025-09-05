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


# 开源AI记忆列表优化更新建议（2025年版）
结合最新开源动态，以下为awesome-ai-memory列表的优化与更新建议，涵盖2025年值得关注的开源AI记忆方案及其分类、存储类型等核心信息。


## 一、更新与补充说明
1.  **新增Basic Memory项目**：采用本地优先架构，基于Markdown文件存储，无需依赖云端即可实现用户与AI的全双向长时记忆，适配注重隐私与本地化部署的场景。
2.  **新增Memories.ai**：聚焦视频记忆的结构化存储与检索，融合向量数据库技术，强化AI对视频内容的记忆能力。
3.  **补充主流开源向量数据库**：新增Chroma、Milvus、Qdrant等方案——这类工具因高性能、强扩展性及丰富索引能力，已成为AI记忆向量数据存储的主流底层支撑。
4.  **保留核心活跃项目**：Cognee、Zep AI、Mem0等现有项目社区活跃度高、关注度持续，继续纳入列表。
5.  **覆盖多元存储需求**：上述项目涵盖内存工具、记忆引擎、向量数据库等多维度，支持图形、向量、多媒体、本地Markdown等多样化存储场景。


## 二、选型建议
1.  **按场景匹配存储类型**：需隐私保护可选用Basic Memory的本地存储；云端智能代理场景可优先选择Mem0或Zep AI。
2.  **适配大规模检索需求**：针对低延迟、大规模记忆检索，建议结合Milvus、Chroma等开源向量数据库作为底层支撑。
3.  **关注项目可持续性**：优先选择社区活跃、技术迭代稳定的项目，确保持续支持能力。


## 三、核心项目说明
以下均为2024-2025年社区认可度高、技术前沿的AI记忆及智能体相关工具：
-  **Mem0**：代表性AI记忆层工具，支持多层次记忆与自适应个性化，解决大模型“记忆断片”问题，具备高效检索与智能更新机制，适配长期记忆与上下文连贯性需求。
-  **Cognee、Zep AI、Memary、Letta (MemGPT)、GraphRAG**：均融合知识图谱与向量存储，支持动态语义记忆与高级推理，适用于构建有状态AI智能体。
-  **Llama Index、LangChain、Haystack**：主流LLM框架，提供强大的向量检索与记忆管理能力，广泛应用于AI智能体及RAG系统。
-  **Neo4j、Weaviate、Milvus、Qdrant、Faiss**：领先的图数据库与向量数据库，支撑高效存储与检索，适配大规模知识及记忆管理场景。
-  **OpenMemory MCP**：最新发布的本地存储与跨工具记忆共享协议，支持多客户端无缝同步，提升多工具协作效率，适合隐私与本地化导向场景。
-  **AutoGPT**：热门AI Agent项目，具备高自主性与模块化设计，集成内存管理功能，支持复杂任务自动执行，适合开发者学习与实践。


本优化方案兼顾主流AI记忆工具与新兴底层向量数据库，贴合2025年技术趋势与应用需求，可根据具体场景进一步定制集成。
