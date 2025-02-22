# Deep Learning-Based Segmentation Model
# 基于深度学习的分割模型

## Introduction / 介绍
This project is based on our research presented in [our ACM paper](https://dl.acm.org/doi/10.1145/3673903). The primary goal of this work is to address the challenge of accurate image segmentation by integrating SPADE normalization and a coattention mechanism. Traditional segmentation models struggle with inconsistent feature representation and ineffective cross-domain feature fusion. Our approach enhances segmentation performance by adapting normalization strategies and refining feature interactions.

本项目基于我们在 [ACM 论文](https://dl.acm.org/doi/10.1145/3673903) 中的研究成果。该研究的主要目标是通过引入 SPADE 归一化和协同注意力机制来提高图像分割的准确性。传统分割模型存在特征表示不稳定和跨域特征融合低效的问题。我们的方法通过优化归一化策略和加强特征交互，提高分割性能。

## Why This Approach? / 为什么采用这种方法？
### Challenge 1: Feature Representation Consistency / 挑战 1：特征表示一致性
Standard normalization techniques fail to preserve spatial details crucial for segmentation. We adopt **SPADE Normalization**, which dynamically adjusts normalization parameters based on segmentation masks, ensuring spatial consistency in feature maps.

标准归一化技术无法有效保留分割任务所需的空间细节。我们采用 **SPADE 归一化**，它基于分割掩码动态调整归一化参数，从而保证特征图的空间一致性。

### Challenge 2: Feature Fusion Across Domains / 挑战 2：跨域特征融合
Multi-source segmentation tasks require effective feature fusion, but conventional methods suffer from misalignment and information loss. Our **Coattention Mechanism** learns to align and weight features dynamically, ensuring better cross-domain interactions and improving segmentation accuracy.

多源分割任务需要高效的特征融合，但传统方法往往存在特征对齐不佳和信息损失的问题。我们的 **协同注意力机制（Coattention Mechanism）** 能够动态学习特征对齐和加权，提高跨域交互效果，从而提升分割准确性。

### Challenge 3: Spatial Alignment in Deformations / 挑战 3：变形情况下的空间对齐
To improve spatial transformations in segmentation tasks, we incorporate **TPS (Thin Plate Spline) Transformation**, allowing the model to handle complex deformations and maintain structure consistency.

为了增强分割任务中的空间变换能力，我们引入 **TPS（薄板样条变换）**，使模型能够处理复杂的形变并保持结构一致性。

## How It Works / 工作原理
### **SPADE Normalization / SPADE 归一化**
Instead of applying global normalization, SPADE learns affine parameters from segmentation maps, enabling adaptive normalization at different spatial locations. This approach retains local structure details and improves segmentation accuracy.

SPADE 不是采用全局归一化，而是从分割掩码中学习仿射变换参数，在不同空间位置自适应调整归一化方式。这种方法可以保留局部结构细节，提高分割精度。

### **Coattention Mechanism / 协同注意力机制**
Our coattention module computes feature correlations between input domains and refines representations based on relevance. This enhances segmentation performance in multi-source scenarios by dynamically focusing on informative regions.

协同注意力模块计算输入域之间的特征相关性，并根据相关性优化特征表示。在多源场景下，该机制能动态关注信息丰富的区域，从而提升分割性能。

### **Hourglass Network for Feature Hierarchy / 特征层次结构的 Hourglass 网络**
To capture multi-scale contextual information, we use a **Hourglass Encoder-Decoder Architecture**, which progressively downsamples and upsamples feature maps, improving object boundary delineation.

为了提取多尺度上下文信息，我们采用 **Hourglass 编码-解码架构**，通过逐步下采样和上采样特征图，提高目标边界的清晰度。

## Features / 主要特性
- **SPADE Normalization / SPADE 归一化**: Spatially adaptive normalization for preserving structural details.
  采用空间自适应归一化方法，保留结构细节。
- **Coattention Mechanism / 协同注意力机制**: Enhances feature alignment and fusion.
  增强特征对齐和融合能力。
- **TPS Transformation / TPS 变换**: Improves handling of spatial deformations.
  提高模型处理空间变形的能力。
- **Hourglass Network / Hourglass 网络**: Captures hierarchical feature representations.
  提取层次化特征表示。
- **Modular Design / 模块化设计**: Easily extendable and customizable components.
  具有良好的扩展性和可定制性。

## Installation / 安装
```sh
# Clone the repository / 克隆仓库
git clone <repo-url>
cd <repo-name>

# Install dependencies / 安装依赖
pip install -r requirements.txt
```

## Usage / 使用方法
### Training / 训练
```sh
python train.py --config config.yaml
```

### Inference / 推理
```sh
python test.py --input input_image.png --output output_image.png
```

## File Structure / 文件结构
- `base_model.py` - Defines the base neural network structure, handling model training, weight loading, and learning rate adjustments.
  `base_model.py` - 定义基础神经网络结构，负责模型训练、权重加载和学习率调整。
- `seg_network.py` - Implements the segmentation model with:
  `seg_network.py` - 实现分割模型，包含：
  - **SPADE Normalization** for spatially adaptive feature modulation.
    **SPADE 归一化**，用于空间自适应特征调整。
  - **Coattention Mechanism** for learning feature alignment dynamically.
    **协同注意力机制**，用于动态学习特征对齐。
- `util.py` - Provides key utilities:
  `util.py` - 提供关键工具函数：
  - **TPS Transformation** for precise spatial adjustments.
    **TPS 变换**，用于精确的空间调整。
  - **Hourglass Network** for hierarchical feature extraction.
    **Hourglass 网络**，用于层次化特征提取。
  - **ResNet Blocks & Normalization Layers** for robust feature learning.
    **ResNet 块和归一化层**，用于增强特征学习能力。

## Citation / 参考文献
If you use this work, please cite:
如果您使用此项目，请引用：
```
@article{your_citation,
  author = {Your Name},
  title = {Deep Learning-Based Segmentation Model},
  journal = {ACM Conference},
  year = {202X},
  doi = {10.1145/3673903}
}
```

## License / 许可证
[Specify License Here / 在此指定许可证]

