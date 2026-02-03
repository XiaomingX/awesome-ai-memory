# Distributed Training & Parameter Consistency

在大规模模型预训练中，确保成百上千个 GPU 之间的模型参数、梯度及优化器状态的一致性是核心挑战。

## 核心框架与工具

| 工具/算法 | 核心开发方 | 并行策略 | 关键特性 |
| :--- | :--- | :--- | :--- |
| **Megatron-LM** | NVIDIA | TP+PP+DP | 高效模型并行预训练，原生支持 GPT/BERT/T5 架构。 |
| **DeepSpeed** | Microsoft | ZeRO 1/2/3 | ZeRO 显存优化技术，支持 3D 并行与大规模模型训练。 |
| **Megatron-DeepSpeed** | Microsoft | 混合并行 | 集成了 Megatron 的并行能力与 DeepSpeed 的显存优化。 |
| **PyTorch FSDP** | Meta | 自动分片 DP | PyTorch 内置的原生全分片数据并行，ZeRO-3 的替代方案。 |
| **ParallelLM** | Community | LoRA 分布式 | 专注于轻量级微调（LoRA/量化）的分布式训练模板。 |

## 实战建议
1. **起步配置**：大规模训练建议从 **Megatron-DeepSpeed** 起步，并开启 **ZeRO-3** 以确保最大程度的参数一致性。
2. **同步机制**：通过 **AllReduce** 算法实现高效的梯度同步，监控 TFLOPs 和损失曲线以防 NaN。
3. **硬件对齐**：在大规模数据（如巴菲特式长文本数据集）训练时，需特别关注多卡之间的负载均衡。
