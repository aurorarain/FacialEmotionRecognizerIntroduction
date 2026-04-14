# FacialEmotionRecognizerIntroduction
  > 实际项目（包含源代码）地址：https://github.com/aurorarain/FacialEmotionRecognizer

  ## 项目简介

  基于深度学习的人脸情绪识别系统，支持图片上传和摄像头实时识别，可识别愤怒、厌恶、恐惧、开心、悲伤、惊讶、中性共 7 种情绪。

  ## 整体架构

  ```
  前端（React + TypeScript）
          ↓ HTTP API
  后端（Java Spring Boot）→ OpenCV 人脸检测
          ↓ ONNX Runtime 推理
  AI 模型（ResNet18 → ONNX 格式）
  ```

  - **前端**：图片上传与摄像头实时识别两种交互方式
  - **后端**：接收请求，调用人脸检测与情绪分类，返回识别结果
  - **AI 推理**：PyTorch 训练的模型导出为 ONNX 格式，通过 ONNX Runtime 在后端直接加载，无需 Python 环境

  ## 训练流程

  - **数据集**：FER2013 公开数据集，约 3.5 万张 48×48 灰度人脸表情图像
  - **模型**：ResNet18 + ImageNet 预训练权重迁移学习
  - **策略**：数据增强、类别加权、过采样、学习率余弦退火、Dropout、早停机制
  - **部署**：PyTorch 模型导出为 ONNX 标准格式，实现训练框架与部署环境解耦

  ## 技术栈

  | 阶段 | 技术 |
  |------|------|
  | 训练 | PyTorch + ResNet18 |
  | 数据集 | FER2013 |
  | 模型部署 | ONNX Runtime |
  | 后端 | Java Spring Boot + OpenCV |
  | 前端 | React + TypeScript |

  ## 作者

  Zhihao_Ji
