# Memory Evaluation Benchmarks

Agent 长期记忆的评测数据集与基准（2026 年重点更新）。评测趋势：从端到端 QA 分数，转向**操作级**（抽取 / 更新 / 遗忘）与**多会话 agentic 行动**。

## 核心基准

| 基准 | 来源 | 评测重点 | 资源 |
| :--- | :--- | :--- | :--- |
| **MemoryAgentBench** | ICLR 2026 | 四维能力解耦：精确检索（AR）、测试时学习（TTL）、长程理解（LRU）、选择性遗忘；新增 EventQA、FactConsolidation | [GitHub](https://github.com/HUST-AI-HYZ/MemoryAgentBench) · [arXiv 2507.05257](https://arxiv.org/abs/2507.05257) |
| **MemoryArena** | ICML 2026 | 多会话 Memory-Agent-Environment 闭环，子任务显式相互依赖（网页导航/偏好规划/渐进搜索/形式推理） | [GitHub](https://github.com/ZexueHe/MemoryArena) · [arXiv 2602.16313](https://arxiv.org/abs/2602.16313) |
| **Memoria-Bench** | ICML 2026 | 长程自主 agent 的情景/语义/程序记忆，覆盖深度研究、代码、表格任务；揭示百万 token 上下文仍存在的记忆瓶颈 | [论文 PDF](https://palm.seu.edu.cn/zhangml/files/ICML%2726a.pdf) |
| **AMA-Bench** | ICML 2026 | 长程 agent 轨迹（状态/动作/观测/工具输出）的长上下文保留与长时程记忆表现 | [GitHub](https://github.com/AMA-Bench/AMA-Bench) · [arXiv 2602.22769](https://arxiv.org/abs/2602.22769) |
| **HaluMem** | arXiv 2025-11 | 首个操作级记忆幻觉基准，拆解记忆抽取 / 更新 / 问答三阶段 | [arXiv 2511.03506](https://arxiv.org/abs/2511.03506) |
| **LongMemEval-V2** | arXiv 2026-05 | web agent 环境经验：静态/动态状态、工作流、坑点、前提感知；历史轨迹最长 115M tokens | [arXiv 2605.12493](https://arxiv.org/abs/2605.12493) |
| **Mem-Gallery** | ACL 2026 | 多模态长程对话记忆，评测 MLLM agent 的抽取/测试时适应、推理、知识管理 | [ACL](https://aclanthology.org/2026.acl-long.1892/) |
| **Mem2ActBench** | ACL 2026 | agent 能否主动用长期记忆驱动工具选择与参数落地（非被动问答） | [ACL](https://aclanthology.org/2026.acl-long.370/) · [GitHub](https://github.com/Cantaloupe-M/Mem2ActBench) |
| **EverMemBench** | arXiv 2026-02 | 多方职场对话，细粒度召回 / 记忆意识 / 用户画像理解 | [arXiv 2602.01313](https://arxiv.org/abs/2602.01313) |
| **Memora** | ACL 2026 | 面向个性化 agent，同时给"该记住"与"该忘记（已删除/更新）"打分，提出 FAMA 指标 | [GitHub](https://github.com/geniesinc/Memora) · [arXiv 2604.20006](https://arxiv.org/abs/2604.20006) |
| **MemoryBench** | arXiv（清华） | 记忆 + 持续学习，on-policy / off-policy 交互模拟 | [arXiv 2510.17281](https://arxiv.org/abs/2510.17281) |
| **BEAM** | ICLR 2026 | 百万 token 级长期记忆的召回与增强 | [arXiv 2510.27246](https://arxiv.org/abs/2510.27246) |
| **LoCoMo** | 2024 | 多会话长对话记忆的经典基线（事件摘要、多跳 QA） | [arXiv 2402.17753](https://arxiv.org/abs/2402.17753) |
| **LongMemEval** | ICLR 2025 | 聊天助手长期记忆：信息抽取、多会话/时序推理、知识更新、拒答 | [arXiv 2410.10813](https://arxiv.org/abs/2410.10813) |
| **memory-benchmarks** | 工具（Mem0 官方） | 开源评测套件，统一跑 LongMemEval / LoCoMo / BEAM 三阶段流水线（Ingest→Search→Evaluate） | [GitHub](https://github.com/mem0ai/memory-benchmarks) |

## 评测方法论提醒

- **检索 > 写入**：`Diagnosing Retrieval vs. Utilization Bottlenecks`（[arXiv 2603.02473](https://arxiv.org/abs/2603.02473)）发现检索质量对最终效果的影响远大于写入/压缩策略，原始分块即可媲美复杂事实抽取。
- **隐藏混淆变量**：`MemDelta`（[arXiv 2606.29914](https://arxiv.org/abs/2606.29914)）指出评测中的隐藏混淆，呼吁使用受控基线，质疑部分结论的可比性。
- **经验质量与错误传播**：`How Memory Management Impacts LLM Agents`（[ACL 2026](https://aclanthology.org/2026.acl-long.27.pdf)）揭示记忆库中错位经验回放会带来负面迁移，主张对经验做质量过滤与历史删除。
- **厂商分数不可直接横比**：LongMemEval / LoCoMo / BEAM 上的公开分数多来自各家自评（如 Mem0 vs Letta），需注意 token 预算与评测协议差异。

## 选型建议

1. **个人助手/客服**：从 LongMemEval + LoCoMo 起步，关注多会话召回与时序推理。
2. **工具型 agent**：用 MemoryAgentBench + Mem2ActBench，检验记忆是否真正驱动行动。
3. **生产稳定性**：用 HaluMem 定位幻觉来源，配合 MemDelta 的受控基线做回归。
4. **多模态场景**：参考 Mem-Gallery，注意显式多模态信息保留与记忆组织。
