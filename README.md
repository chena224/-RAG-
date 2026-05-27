# 📚 基于 RAG 的长春工业大学校园校规问答助手

> 一个完整的检索增强生成（RAG）系统：上传 PDF 文档，基于 LangChain + FAISS + DeepSeek API 实现智能问答，支持多轮对话，提供 Gradio Web 界面与公网访问。

## ✨ 功能特点

- 🔍 **PDF 智能问答**：上传校规、手册等 PDF 文档，系统自动切分、向量化，并基于文档内容回答问题。
- 🧠 **多轮对话记忆**：支持上下文连续对话，可以追问细节。
- 🌐 **公网访问**：通过 ngrok 提供临时公网链接，方便面试官或朋友在线体验。
- ⚡ **快速响应**：使用轻量级中文嵌入模型 `BAAI/bge-small-zh-v1.5` + FAISS 向量检索，保证速度与效果。

## 🛠️ 技术栈

| 组件 | 技术 |
|------|------|
| 大模型 | DeepSeek-v4-pro (API) |
| 嵌入模型 | BAAI/bge-small-zh-v1.5 (本地) |
| 向量数据库 | FAISS (CPU版) |
| 应用框架 | LangChain + LCEL |
| 前端界面 | Gradio |
| 内网穿透 | ngrok / Gradio share |
| 语言 | Python 3.10+ |

## 📁 项目结构
.
├── rag_app.py # 主程序
├── requirements.txt # 依赖列表
├── README.md # 项目说明
├── faiss_index/ # FAISS 索引目录（自动生成）
└── models/ # 本地嵌入模型（可选，也可自动下载）

## 🚀 快速开始

### 1. 环境要求

- Python 3.10+
- （可选）Docker（用于公网访问）

### 2. 安装依赖

```bash
pip install -r requirements.txt
3. 配置 API 密钥
本项目使用 DeepSeek API，你需要注册并获取 API Key。

注册：DeepSeek 开放平台

获取 api_key，然后在代码中设置（或通过环境变量）

在 rag_app.py 中找到 API_KEY = "sk-..." 并替换为你自己的密钥。

4. 准备文档
将你想要问答的 PDF 文件放在指定路径，例如 D:\docs\school_rules.pdf，然后修改脚本开头的 PDF_PATH 变量。

5. 运行项目
bash

复制

下载
python rag_app.py
首次运行会自动：

加载并切分 PDF

下载嵌入模型（若本地没有）

构建 FAISS 索引

启动 Gradio 本地服务（http://localhost:7860）

看到类似输出即为成功：

text

复制

下载
* Running on local URL:  http://0.0.0.0:7860
6. 公网访问
https://gating-elevate-uneasily.ngrok-free.dev/
