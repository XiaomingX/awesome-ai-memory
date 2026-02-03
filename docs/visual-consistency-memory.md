# Visual Consistency & Generation Memory

专注于在大模型生成图片和视频时，如何通过特定技术维持人物、角色及艺术风格的一致性。

## 核心推荐项目

| 项目名称 | 核心算法 | 关键特性 |
| :--- | :--- | :--- |
| **StoryMaker** | 参考图像注入 + 注意力融合 | 保持脸部、服装、发型高度一致，支持复杂的故事序列生成。 |
| **ConsistI2V** | 时空注意力 + 低频噪声初始化 | Image-to-Video 一致性，维持布局与运动的连贯性。 |
| **CharacterFactory** | GAN 嵌入 + 上下文一致损失 | 无限新角色采样，端到端与扩散模型集成。 |
| **IP-Adapter** | 图像提示适配器 | 轻量级参考注入，跨模型风格一致，支持 ComfyUI 扩展。 |
| **TheaterGen** | LLM 角色管理 + 一致性评估 | 多轮图像生成一致性，支持动态人物库管理。 |

## 集成建议
1. **工作流选择**：优先将 StoryMaker 或 IP-Adapter 集成到 ComfyUI 中。
2. **训练策略**：先通过 Textual Inversion 或 LoRA 锁定参考脸部嵌入，再生成序列。
3. **控制技巧**：结合 ControlNet 姿势引导，确保视频帧与帧之间的绝对连贯。
