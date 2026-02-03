# LLM Pre-training & Memory Architecture Research

聚焦于预训练阶段增强大模型原生记忆能力的算法、论文及框架。

## 核心算法与研究

- **Titans: Learning to Memorize at Test Time**：Google 提出，在预训练中引入神经记忆模块。
- **Ultra-Sparse Memory Network**：通过稀疏记忆网络优化内存使用与回忆效率。
- **Rethinking Reflection in Pre-Training**：探索将反思机制融入预训练。
- **Knowledge-Instruct**：利用知识指令进行持续预训练以增强记忆。

## 优质研究专栏

| 仓库名称 | 焦点内容 |
| :--- | :--- |
| **Awesome LLM Pre-training** | 预训练策略、架构改进（如 Titans、Ultra-Sparse）。 |
| **Awesome-AI-Memory** | 多种 AI 记忆机制扩展 LLM 上下文。 |
| **Memory Efficient Pretraining** | 内存高效预训练框架与算法实验。 |

## 实现建议
- **框架选择**：建议从 Megatron-LM 等成熟框架起步。
- **成本考量**：优先测试稀疏记忆（Sparse Memory）以降低计算成本。
