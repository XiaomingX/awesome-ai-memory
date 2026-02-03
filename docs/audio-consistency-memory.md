# Audio Consistency & Style Memory

通过参考音频注入、嵌入提取等技术，确保 LLM 生成的音频（语音、音乐）在音色、风格上保持高度一致。

## 核心推荐项目

| 项目名称 | 核心算法 | 关键特性 |
| :--- | :--- | :--- |
| **Amphion** | Vevo 零样本声模仿 | TTS/VC 领域 SOTA 表现，支持极高质量的音色克隆与风格迁移。 |
| **Bark** | Transformer TTS | 语义 Token 一致性，支持多语言、多说话者的高真实感生成。 |
| **FunMusic** | 令牌自回归 + 流匹配 | 长形式音乐生成，保证音律与风格的跨片段连贯。 |
| **Parler-TTS** | 描述器控制 + 种子固定 | 保证 Speaker Prompt 嵌入的一致性，支持音调/语速精准控制。 |
| **CoMoSpeech** | 一致性模型 (Consistency Model) | 单步采样实现高质量生成，超实时推理速度。 |

## 集成建议
1. **音色维护**：利用 Amphion 的 Vevo 模块进行 Speaker Embedding 提取。
2. **长文本配音**：在生成小说音频序列时，通过固定种子 (Seed) 和 Speaker Prompt 嵌入来保证音色稳定。
3. **性能监控**：重点测试 MOS (平均主观意见分) 以评估自然度，并控制 RTF (实时率) 以满足实时需求。
