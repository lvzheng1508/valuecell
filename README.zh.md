<p align="center">
  <img src="assets/valuecell.png" style="width: 100%; height: auto;">
</p>

<div align="center" style="line-height: 2;">
    <a href="https://www.python.org/downloads" target="_blank">
        <img src="https://img.shields.io/badge/python-3.12+-blue.svg"
            alt="Python version"></a>
    <a href="LICENSE" target="_blank">
        <img src="https://img.shields.io/badge/license-Apache2.0-red.svg"
            alt="License: Apache2.0"></a>  
    <br>
    <a href="https://discord.com/invite/84Kex3GGAh" target="_blank">
        <img src="https://img.shields.io/discord/1399603591471435907?logo=discord&labelColor=%20%235462eb&logoColor=%20%23f5f5f5&color=%20%235462eb"
            alt="chat on Discord"></a>
    <a href="https://twitter.com/intent/follow?screen_name=valuecell" target="_blank">
        <img src="https://img.shields.io/twitter/follow/valuecell?logo=X&color=%20%23f5f5f5"
            alt="follow on X(Twitter)"></a>
    <a href="https://www.linkedin.com/company/valuecell/" target="_blank">
        <img src="https://custom-icon-badges.demolab.com/badge/LinkedIn-0A66C2?logo=linkedin-white&logoColor=fff"
            alt="follow on LinkedIn"></a>
    <a href="https://www.facebook.com/people/ValueCell/61581410516790/" target="_blank">
        <img src="https://custom-icon-badges.demolab.com/badge/Facebook-1877F2?logo=facebook-white&logoColor=fff"
            alt="follow on Facebook"></a>
</div>

<div align="center">
  <a href="README.md" style="color: gray;">English</a>
  <a href="README.zh.md" style="color: gray;">中文（简体）</a>
  <a href="README.zh_Hant.md" style="color: auto;">中文（繁體）</a>
  <a href="README.ja.md" style="color: gray;">日本語</a>
</div>

# ValueCell

ValueCell 是一个社区驱动的多智能体金融应用平台。

它将为您提供顶级的投资智能体团队，帮助您管理投资组合。

# 产品截图

<p align="center">
  <img src="assets/product/homepage.png" style="width: 100%; height: auto;">
</p>

<p align="center">
  <img src="assets/product/agent_market.png" style="width: 100%; height: auto;">
</p>

<p align="center">
  <img src="assets/product/superagent.png" style="width: 100%; height: auto;">
</p>

<p align="center">
  <img src="assets/product/AutoTradingAgent.png" style="width: 100%; height: auto;">
</p>

# 核心特性

<p align="center">
  <img src="assets/architecture.png" style="width: 100%; height: auto;">
</p>

## 多智能体系统

- **DeepResearch Agent**: 获取并分析股票的 SEC 文件，输出准确的数据、可解释性的总结
- **Auto Trading Agent**: 支持多种加密资产和 AI 自动交易策略
- **Trading Agents**：专门负责市场分析、情绪分析、新闻分析和基本面分析的智能体协同工作
- **AI-Hedge-Fund**：智能体协作提供全面的金融洞察
- **其他智能体**：更多智能体正在规划中...

## 灵活集成

- **多种大语言模型提供商**：支持 OpenRouter、OpenAI、Anthropic、Google 和 Ollama
- **热门市场数据**：覆盖美国市场、加密货币市场、香港市场、中国市场等
- **多智能体框架兼容**：通过 A2A 协议，支持 Langchain、Agno 等主流 Agent 框架

# 快速开始

ValueCell 是一个基于 Python 的应用程序，且有完备的前端操作页面。可以参考下面配置快速运行。

## 前提条件

为了获得最佳性能和简化开发，我们建议安装以下工具：

**[uv](https://docs.astral.sh/uv/getting-started/installation/)** - 用 Rust 构建的超快速 Python 包和项目管理器  
**[bun](https://github.com/oven-sh/bun#install)** - 高性能 JavaScript/TypeScript 工具包，集成运行时、打包器、测试运行器和包管理器

## 安装

1. **克隆仓库**

   ```bash
   git clone https://github.com/ValueCell-ai/valuecell.git
   cd valuecell
   ```

2. **配置环境变量**

   ```bash
   cp .env.example .env
   ```

   使用您的 API 密钥和偏好设置编辑`.env`文件。此配置文件在所有智能体之间共享。详见 [配置指南](docs/CONFIGURATION_GUIDE.md)。

## 配置

### 模型提供商

通过编辑`.env`文件配置您首选的模型提供商：

- **主要支持**：[OpenRouter](https://openrouter.ai) - 目前大多数智能体的主要支持提供商
- **TradingAgents** 集成了 Memory 功能。如果您使用 OpenRouter 作为 API 密钥，需要配置嵌入模型参数（因为 OpenRouter 不支持嵌入模型）。请参考 TradingAgents/.env.example 文件，并将其配置复制到根目录的.env 文件中。

根据您的需求和使用模式选择首选的模型和提供商。

## 运行应用程序

启动完整的应用程序堆栈（前端、后端和智能体）：

```bash
bash start.sh
```

## 访问界面

- **Web UI**：在浏览器中导航到 [http://localhost:1420](http://localhost:1420)
- **日志**：在 `logs/{timestamp}/*.log` 监控应用程序日志，获取后端服务和各个智能体的详细运行时信息

## 最后

应用程序运行后，您可以通过 Web 界面使用 ValueCell 中集成的 Agents。

---

**注意**：运行应用程序前，请确保所有前提条件已安装且环境变量已正确配置。

# 问题排查与常见问题

本节提供在 ValueCell 设置和启动过程中遇到的常见问题的解决方案。

## 前提条件检查

在开始之前，请确保已安装所需的工具：

```bash
# 检查工具是否已安装
which bun && echo "✅ bun 已安装" || echo "❌ bun 未安装"
which uv && echo "✅ uv 已安装" || echo "❌ uv 未安装"
which python3 && echo "✅ python3 已安装" || echo "❌ python3 未安装"

# 检查 Python 版本
python3 --version
```

## 常见启动问题及解决方案

### 1. 缺少依赖包

**症状**：各种包的 `ModuleNotFoundError` 错误

**解决方案**：手动安装缺少的依赖：

```bash
cd python
source .venv/bin/activate

# 安装核心依赖
pip install fastapi uvicorn yfinance akshare requests sqlalchemy aiosqlite loguru aiofiles

# 安装 AI/Agent 依赖
pip install agno unstructured markdown pytz python-dateutil

# 安装缺少的 SDK 依赖
pip install 'a2a-sdk[http-server]' google-genai lancedb

# 安装网页爬虫依赖
pip install crawl4ai==0.7.4 edgartools
```

### 2. 数据库初始化问题

**症状**：API 端点（如 `/api/v1/watchlist/` 或 `/api/v1/agents/`）返回 500 内部服务器错误

**解决方案**：初始化数据库表：

```bash
cd python
source .venv/bin/activate
python -m valuecell.server.db.init_db --force
```

这将：

- 创建所有必要的数据库表
- 初始化默认智能体（ResearchAgent、AutoTradingAgent 等）
- 添加默认资产（NASDAQ:IXIC、HKEX:HSI、SSE:000001）

### 3. 平台兼容性问题

**症状**：在 macOS x86_64 上 `pylance` 包安装失败

**解决方案**：这是 Intel Mac 上 `pylance` 的已知问题。项目可以在没有此可选依赖的情况下正常工作。使用 `pip` 而不是 `uv` 进行依赖安装。

### 4. Playwright/Chromium 问题

**症状**：Chromium 下载卡住或失败

**解决方案**：删除锁文件并重试：

```bash
# 删除 Playwright 锁文件
rm -rf /Users/lvzheng/Library/Caches/ms-playwright/__dirlock
rm -rf ~/.cache/ms-playwright/__dirlock

# 或者使用系统 Chromium
PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD=1 bash start.sh
```

### 5. LLM 配置问题

**症状**：Agent API 超时或错误

**解决方案**：验证您的 `.env` 配置：

```bash
# 检查 API 密钥是否设置
grep -E "OPENROUTER|EMBEDDER" .env

# 测试 LLM 连接
cd python && source .venv/bin/activate
python -c "from valuecell.utils.model import get_model; print('✅ LLM 模型已加载:', type(get_model('RESEARCH_MODEL_ID')))"

# 测试 Embedding
python -c "from valuecell.agents.research_agent.vdb import embedder; result = embedder.get_embedding('test'); print(f'✅ Embedding 工作正常，维度: {len(result)}')"
```

### 6. 手动启动（start.sh 的替代方案）

如果 `start.sh` 失败，您可以手动启动服务：

```bash
# 终端 1：后端
cd python && source .venv/bin/activate
python -m valuecell.server.main

# 终端 2：前端
cd frontend
bun run dev
```

### 7. 端口冲突

**症状**：由于端口冲突导致服务启动失败

**解决方案**：检查并释放占用的端口：

```bash
# 检查端口使用情况
lsof -i :8000  # 后端端口
lsof -i :1420  # 前端端口

# 如果需要，终止进程
pkill -f "python.*valuecell.server.main"
pkill -f "bun.*dev"
```

## 验证步骤

设置完成后，验证一切是否正常工作：

```bash
# 测试后端 API
curl -s http://localhost:8000/api/v1/watchlist/asset/search?q=AAPL | head -3

# 测试 Agent API
curl -s http://localhost:8000/api/v1/agents/?enabled_only=true | head -3

# 检查前端
curl -s http://localhost:1420 | head -5
```

预期响应：

- 后端：应返回包含股票数据的 JSON
- Agent：应返回启用的智能体列表
- 前端：应返回 HTML 内容

## 环境变量参考

确保您的 `.env` 文件包含：

```bash
# OpenRouter（主要 LLM 提供商）
OPENROUTER_API_KEY=您的_openrouter_密钥

# Embedding（TradingAgents 必需）
EMBEDDER_API_KEY=您的_embedding_密钥
EMBEDDER_BASE_URL=https://dashscope.aliyuncs.com/compatible-mode/v1
EMBEDDER_MODEL_ID=text-embedding-v3
EMBEDDER_DIMENSION=1536

# 可选：其他模型提供商
OPENAI_API_KEY=您的_openai_密钥
ANTHROPIC_API_KEY=您的_anthropic_密钥
GOOGLE_API_KEY=您的_google_密钥
```

## 获取帮助

如果您遇到此处未涵盖的问题：

1. 检查 `logs/` 目录中的应用程序日志
2. 查看后端控制台输出以获取错误消息
3. 确保所有依赖项已正确安装
4. 验证 API 密钥有效且具有足够的配额

---

# Roadmap

## 🤖 增强智能体能力

### 市场扩展

- **欧洲市场**：增加对富时指数、DAX、CAC 40 和其他欧洲交易所的支持
- **亚洲市场**：扩展对日经指数、恒生指数、上证综指和新兴亚洲市场的覆盖
- **大宗商品市场**：石油、黄金、白银、农产品分析
- **外汇市场**：主要货币对和交叉货币分析

### 资产类别多样化

- **固定收益**：政府债券、企业债券和收益率分析智能体
- **衍生品**：期权、期货和复杂金融工具
- **另类投资**：私募股权、对冲基金和风险投资分析

### 高级通知和推送类型

- **实时警报**：价格变动、成交量激增和技术突破
- **定期报告**：每日/每周/每月投资组合摘要
- **事件驱动通知**：财报发布、股息公告、监管变化
- **自定义触发器**：用户定义的条件和阈值
- **多渠道推送**：邮件、短信、Slack、Discord 和 webhook 集成

## ⚙️ 产品配置与个性化

### 国际化 (i18n)

- **多语言支持**：英语、中文（简体/繁体）、日语、韩语、西班牙语、法语
- **本地化市场数据**：特定地区的金融术语和格式
- **文化适应**：时区、日期格式和货币偏好
- **智能体个性本地化**：文化适宜的沟通风格

### 令牌和身份验证管理

- **API 密钥管理**：第三方 API 密钥的安全存储和轮换
- **OAuth 集成**：支持主要金融数据提供商
- **速率限制**：智能请求节流和配额管理
- **多租户架构**：企业级用户隔离和安全

### 用户偏好和自定义

- **投资档案**：风险承受能力、投资期限和策略偏好
- **UI/UX 自定义**：深色/浅色模式、仪表板布局和小部件偏好
- **智能体行为**：沟通频率、分析深度和报告风格
- **投资组合管理**：自定义基准、绩效指标和配置目标

### 记忆和学习系统

- **对话历史**：跨会话的持久聊天历史
- **用户学习**：基于用户行为的自适应推荐
- **市场记忆**：历史背景和模式识别
- **偏好演进**：推荐的动态调整

## 🔧 ValueCell SDK 开发

### 核心 SDK 功能

- **Python SDK**：用于智能体集成和自定义的核心代码，衔接前后端
- **REST API 包装器**：具有自动身份验证的简化 HTTP 客户端
- **WebSocket 支持**：实时数据流和双向通信

### 智能体集成框架

- **插件架构**：轻松集成第三方智能体和工具
- **智能体注册表**：社区贡献智能体的市场
- **自定义智能体构建器**：低代码/无代码智能体创建工具
- **智能体编排**：工作流管理和智能体协调

### 开发者工具和文档

- **交互式 API 浏览器**：带有实时测试的 Swagger/OpenAPI 文档
- **代码示例**：多种编程语言的示例实现
- **测试框架**：单元测试、集成测试和模拟数据提供商

# Star

<div align="center">
<a href="https://www.star-history.com/#ValueCell-ai/valuecell&Date">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=ValueCell-ai/valuecell&type=Date&theme=dark" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=ValueCell-ai/valuecell&type=Date" />
   <img alt="TradingAgents Star History" src="https://api.star-history.com/svg?repos=ValueCell-ai/valuecell&type=Date" style="width: 80%; height: auto;" />
 </picture>
</a>
</div>

<div align="center">
