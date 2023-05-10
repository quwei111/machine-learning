# 多模态

单流模型和双流模型
- 单流模型将图像侧和文本侧的embedding拼接到一起，输入到一个Transformer模型中。
- 双流模型让图像侧和文本侧使用两个独立的Transformer分别编码，可以在中间层加入两个模态之间的Attention来融合多模态信息



多模态对齐
- 借鉴BERT的思想进行masked language modeling对齐
- 使用contrastive loss进行多模态对齐

VILBERT

CLIP

- ALBEF
- BLIP
