# TCMIIES - 传统中医药医学信息智能提取系统

**Traditional Chinese Medicine Information Intelligent Extraction System**

河北大学中医药信息学实验室 · 论文信息智能提取系统

---

## 简介

TCMIIES 是一款基于大语言模型（LLM）的纯前端论文信息智能提取工具。系统能够批量读取从中国知网、万方等数据库导出的论文数据文件（Excel/CSV），通过调用 AI 大模型 API 自动提取论文中的关键信息（如研究主题、研究方法、创新点、主要结论等），并将结构化结果导出为 Excel、CSV 或 JSON 文件。

## 核心特点

- **纯前端运行** — 所有数据处理在浏览器本地完成，无需安装软件，无需后端服务器
- **数据安全** — 论文数据和 API Key 仅存储在用户浏览器本地，不经过任何第三方服务器
- **多服务商支持** — DeepSeek、OpenAI、通义千问（阿里云）、智谱AI 及自定义 OpenAI 兼容接口
- **智能字段识别** — 自动识别知网导出文件的常见列名（篇名、摘要、关键词等）
- **批量高效处理** — 并发控制、暂停/继续、失败自动重试
- **灵活配置** — 自定义提取字段、提示词模板，支持预览和单条测试
- **多格式导出** — Excel (.xlsx)、CSV、JSON 三种格式

## 系统工作流程

```
配置API → 上传数据 → 配置提取字段 → 执行提取 → 导出结果
```

## 快速开始

### 环境要求

| 项目 | 要求 |
|------|------|
| 浏览器 | Chrome 90+、Edge 90+、Firefox 90+、Safari 14+ |
| 网络 | 需要访问 CDN（加载 Vue3 和 SheetJS）及 AI 服务商 API |
| 数据文件 | 支持 .xlsx、.xls、.csv 格式 |
| API Key | 至少一个支持的 AI 服务商 API Key |

### 启动方式

**方式一：直接打开**

双击 `index.html` 文件，在浏览器中即可使用。

**方式二：本地服务器（推荐）**

```bash
# 在项目目录下执行
python -m http.server 8080
```

然后浏览器访问 `http://localhost:8080`

## 使用说明

详细使用说明请参阅 [使用说明书.html](./使用说明书.html)，可在浏览器中直接打开查看。

### 简要步骤

1. **API 配置** — 选择 AI 服务商，填写 API Key，选择模型，测试连接
2. **数据上传** — 拖拽或点击上传从数据库导出的 Excel/CSV 文件
3. **提取配置** — 设置提取字段（可使用预设模板），编辑提示词
4. **执行任务** — 点击"开始提取"，实时监控进度，支持暂停/继续/取消
5. **结果导出** — 查看提取结果，支持内联编辑，导出为 Excel/CSV/JSON

## 支持的 AI 服务商

| 服务商 | 模型 | 特点 |
|--------|------|------|
| **DeepSeek**（默认） | deepseek-v4-pro, deepseek-v4-flash, deepseek-chat, deepseek-reasoner | 国内直连、性价比高、新用户赠送额度 |
| **OpenAI** | gpt-4o, gpt-4o-mini, gpt-4.1, gpt-4.1-mini, gpt-4.1-nano | 国际领先模型，可能需代理 |
| **通义千问** | qwen-max, qwen-plus, qwen-turbo, qwen-long | 阿里云模型，国内直连 |
| **智谱AI** | glm-4-plus, glm-4-air, glm-4, glm-4-flash | 国内直连，glm-4-flash 免费 |
| **自定义** | 用户自定义 | 兼容 OpenAI API 格式的任意服务商 |

## 技术栈

- **Vue 3** — 响应式前端框架
- **SheetJS (XLSX)** — Excel/CSV 文件解析与生成
- **Fetch API** — 直接调用 OpenAI 兼容 API
- 纯 HTML/CSS/JS 单文件架构，零构建依赖

## 项目结构

```
TCMIIES/
├── index.html          # 系统主文件（包含全部功能代码）
├── 使用说明书.html      # 详细使用说明书
└── README.md           # 项目说明文档
```

## 安全与隐私

- 所有论文数据仅在浏览器本地处理
- API Key 使用 Base64 编码存储在浏览器 localStorage
- 数据仅发送至用户选择的 AI 服务商 API，不经过中间环节
- 提供一键清除所有本地数据功能

## 许可证

BSD 3-Clause License

## 引用信息

ZHAO H. TCMIIES: A Browser-Based LLM-Powered Intelligent Information Extraction System for Academic Literature[EB/OL]. (2026-05-08). https://doi.org/10.48550/arXiv.2605.07507.

---
> 河北大学中医药信息学实验室
