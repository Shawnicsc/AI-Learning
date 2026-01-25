# AI 大模型应用开发笔记

## 一、 大语言模型基础

### 1.1 Markov Assumption

概念：一个词出现的概率只与它前`N-1`个词有关。`N->上下文窗口` 

计算：条件概率 + 全概率公式

### 1.2 神经网络与词嵌入

1. 构建语义空间：创建一个高维的连续向量空间，每个词映射到该空间（word embedding）
2. 学习从上下文到下一个词的映射

通过此方式，可用余弦相似度度量关系\( similarity(a,b) = cos(\theta)\) 

- 如果两个向量方向完全相同，夹角为0°，余弦值为1，表示完全相关。
- 如果两个向量方向正交，夹角为90°，余弦值为0，表示毫无关系。
- 如果两个向量方向完全相反，夹角为180°，余弦值为-1，表示完全负相关。

### 1.3 RNN & LSTM

`RNN` ：循环神经网络，为神经网络添加‘记忆’功能

`LSTM`：长短时记忆网络，为解决`RNN`长期依赖问题

- 细胞状态+门控机制
- **遗忘门 (Forget Gate)**：决定从上一时刻的细胞状态中丢弃哪些信息。
- **输入门 (Input Gate)**：决定将当前输入中的哪些新信息存入细胞状态。
- **输出门 (Output Gate)**：决定根据当前的细胞状态，输出哪些信息到隐藏状态。

### 1.4 Transformer 架构

```txt
Attention is all you need
```

## 二、Agent

### 2.1 框架

- AutoGen
- LangGraph

### 2.2 记忆与检索

### 2.3 Context



## 三、毕业设计

**以项目驱动学习 **

选题： **智能笔记——`FreeNote-Assistant`

### 需求分析

- 类 typora 功能，自由编辑markdown文本，“所见即所得”
- 支持对当前文档生成UML图 || 总结 summary
- 支持对当前文档进行润色修改
- 知识库检索，将当前文件夹所有文档作为知识库，通过检索回答问题（隐性功能：对话功能）
- 导入导出功能
- 支持用户自己添加ai源，配置api_key

### 技术选型

桌面应用 —— `Tauri`

Markdown 编辑器 

| 能力          | 技术选型          |
| ------------- | ----------------- |
| 所见即所得    | ProseMirror       |
| Markdown 编辑 | Milkdown / TipTap |
| UML 预览      | Mermaid           |
| 代码高亮      | Prism.js          |

后端API框架 —— `fastapi`

数据存储：

| 数据类型 | 技术                     |
| -------- | ------------------------ |
| 文档内容 | 本地文件系统（Markdown） |
| 元数据   | SQLite                   |
| 配置     | YAML / JSON              |
| API Key  | 本地加密存储             |

大模型技术

调用框架—— `LangChain`

 prompt模板 —— `Jinja2`

长文档处理 —— `Map-Reduce Summarization`

风格控制 —— `Prompt Engineering`

RAG：

| 模块       | 技术                           |
| ---------- | ------------------------------ |
| 文档切分   | RecursiveCharacterTextSplitter |
| 向量模型   | text-embedding / BGE           |
| 向量数据库 | **Chroma / FAISS**             |
| 检索策略   | Similarity / MMR               |

Chat：

| 组件       | 技术               |
| ---------- | ------------------ |
| 会话记忆   | ConversationBuffer |
| 上下文构建 | Top-K 文档         |
| 回答生成   | LLM                |

### 开发任务清单



