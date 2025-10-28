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

ValueCell is a community-driven, multi-agent platform for financial applications.

It provides a team of TOP investment Agents to help manage your portfolio.

# Screenshot

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

# Key Features

<p align="center">
  <img src="assets/architecture.png" style="width: 100%; height: auto;">
</p>

## Multi-Agent System

- **DeepResearch Agent**: Automatically retrieve and analyze SEC filings to generate accurate data insights and interpretable summaries
- **Auto Trading Agent**: multiple crypto assets and AI-powered trading strategies
- **Trading Agents**: Agents work for market analysis, sentiment analysis, news analysis, and fundamentals analysis
- **AI-Hedge-Fund**: Agents collaborate to provide comprehensive financial insights
- **Others**: More agents are in planning...

## Flexible Integrations

- **Multiple LLM Providers**: Support OpenRouter, OpenAI, Anthropic, Google and Ollama
- **Popular Market Data**: Cover US market, Crypto market, Hong Kong market, China market and more
- **Multi-Agent Framework Compatible**: Support Langchain, Agno by A2A Protocol

# Quick Start

ValueCell is a Python-based application featuring a comprehensive web interface. Follow this guide to set up and run the application efficiently.

## Prerequisites

For optimal performance and streamlined development, we recommend installing the following tools:

**[uv](https://docs.astral.sh/uv/getting-started/installation/)** - Ultra-fast Python package and project manager built in Rust  
**[bun](https://github.com/oven-sh/bun#install)** - High-performance JavaScript/TypeScript toolkit with runtime, bundler, test runner, and package manager

## Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/ValueCell-ai/valuecell.git
   cd valuecell
   ```

2. **Configure environment variables**

   ```bash
   cp .env.example .env
   ```

   Edit the `.env` file with your API keys and preferences. This configuration file is shared across all agents. See [Configuration Guide](docs/CONFIGURATION_GUIDE.md) for details.

## Configuration

### Model Providers

Configure your preferred model providers by editing the ⁠`.env` file:

- **Primary Support**: [OpenRouter](https://openrouter.ai) - Currently the main supported provider for most agents
- **TradingAgents** requires the use of Memory. If you use OpenRouter as API key, configuring the Embedding model parameters will be needed (since OpenRouter does not support Embedding models). Please refer to the TradingAgents/.env.example file and copy its configuration into the .env file located in the root directory.

Choose your preferred models and providers based on your requirements and preferences.

## Running the Application

Launch the complete application stack (frontend, backend, and agents):

### Linux / Macos

```bash
bash start.sh
```

### Windows (PowerShell)

```powershell
.\start.ps1
```

## Accessing the Interface

- **Web UI**: Navigate to [http://localhost:1420](http://localhost:1420) in your browser
- **Logs**: Monitor application logs at `logs/{timestamp}/*.log` for detailed runtime information of backend services and individual agents

## Next Steps

Once the application is running, you can explore the web interface to interact with ValueCell's features and capabilities.

---

**Note**: Ensure all prerequisites are installed and environment variables are properly configured before running the application.

# Troubleshooting & Common Issues

This section provides solutions to common problems encountered during ValueCell setup and startup.

## Prerequisites Check

Before starting, ensure you have the required tools installed:

```bash
# Check if tools are installed
which bun && echo "✅ bun is installed" || echo "❌ bun not installed"
which uv && echo "✅ uv is installed" || echo "❌ uv not installed"
which python3 && echo "✅ python3 is installed" || echo "❌ python3 not installed"

# Check Python version
python3 --version
```

## Common Startup Issues and Solutions

### 1. Missing Dependencies

**Symptoms**: `ModuleNotFoundError` for various packages

**Solution**: Install missing dependencies manually:

```bash
cd python
source .venv/bin/activate

# Install core dependencies
pip install fastapi uvicorn yfinance akshare requests sqlalchemy aiosqlite loguru aiofiles

# Install AI/Agent dependencies
pip install agno unstructured markdown pytz python-dateutil

# Install missing SDK dependencies
pip install 'a2a-sdk[http-server]' google-genai lancedb

# Install crawl4ai for web scraping
pip install crawl4ai==0.7.4 edgartools
```

### 2. Database Initialization Issues

**Symptoms**: 500 Internal Server Error on API endpoints like `/api/v1/watchlist/` or `/api/v1/agents/`

**Solution**: Initialize the database tables:

```bash
cd python
source .venv/bin/activate
python -m valuecell.server.db.init_db --force
```

This will:

- Create all necessary database tables
- Initialize default agents (ResearchAgent, AutoTradingAgent, etc.)
- Add default assets (NASDAQ:IXIC, HKEX:HSI, SSE:000001)

### 3. Platform Compatibility Issues

**Symptoms**: `pylance` package installation fails on macOS x86_64

**Solution**: This is a known issue with `pylance` on Intel Macs. The project will work without this optional dependency. Use `pip` instead of `uv` for dependency installation.

### 4. Playwright/Chromium Issues

**Symptoms**: Chromium download hangs or fails

**Solution**: Remove lock files and retry:

```bash
# Remove Playwright lock files
rm -rf /Users/lvzheng/Library/Caches/ms-playwright/__dirlock
rm -rf ~/.cache/ms-playwright/__dirlock

# Or use system Chromium instead
PLAYWRIGHT_SKIP_BROWSER_DOWNLOAD=1 bash start.sh
```

### 5. LLM Configuration Issues

**Symptoms**: Agent API timeouts or errors

**Solution**: Verify your `.env` configuration:

```bash
# Check if API keys are set
grep -E "OPENROUTER|EMBEDDER" .env

# Test LLM connectivity
cd python && source .venv/bin/activate
python -c "from valuecell.utils.model import get_model; print('✅ LLM model loaded:', type(get_model('RESEARCH_MODEL_ID')))"

# Test Embedding
python -c "from valuecell.agents.research_agent.vdb import embedder; result = embedder.get_embedding('test'); print(f'✅ Embedding works, dimension: {len(result)}')"
```

### 6. Manual Startup (Alternative to start.sh)

If `start.sh` fails, you can start services manually:

```bash
# Terminal 1: Backend
cd python && source .venv/bin/activate
python -m valuecell.server.main

# Terminal 2: Frontend
cd frontend
bun run dev
```

### 7. Port Conflicts

**Symptoms**: Services fail to start due to port conflicts

**Solution**: Check and free occupied ports:

```bash
# Check port usage
lsof -i :8000  # Backend port
lsof -i :1420  # Frontend port

# Kill processes if needed
pkill -f "python.*valuecell.server.main"
pkill -f "bun.*dev"
```

## Verification Steps

After setup, verify everything is working:

```bash
# Test backend API
curl -s http://localhost:8000/api/v1/watchlist/asset/search?q=AAPL | head -3

# Test agent API
curl -s http://localhost:8000/api/v1/agents/?enabled_only=true | head -3

# Check frontend
curl -s http://localhost:1420 | head -5
```

Expected responses:

- Backend: Should return JSON with stock data
- Agents: Should return list of enabled agents
- Frontend: Should return HTML content

## Environment Variables Reference

Make sure your `.env` file contains:

```bash
# OpenRouter (Primary LLM provider)
OPENROUTER_API_KEY=your_openrouter_key_here

# Embedding (Required for TradingAgents)
EMBEDDER_API_KEY=your_embedding_key_here
EMBEDDER_BASE_URL=https://dashscope.aliyuncs.com/compatible-mode/v1
EMBEDDER_MODEL_ID=text-embedding-v3
EMBEDDER_DIMENSION=1536

# Optional: Other model providers
OPENAI_API_KEY=your_openai_key_here
ANTHROPIC_API_KEY=your_anthropic_key_here
GOOGLE_API_KEY=your_google_key_here
```

## Getting Help

If you encounter issues not covered here:

1. Check the application logs in `logs/` directory
2. Review backend console output for error messages
3. Ensure all dependencies are installed correctly
4. Verify API keys are valid and have sufficient quotas

---

# Roadmap

## 🤖 Enhanced Agent Capabilities

### Market Expansion

- **European Markets**: Add support for FTSE, DAX, CAC 40, and other European exchanges
- **Asian Markets**: Expand coverage to Nikkei, Hang Seng, Shanghai Composite, and emerging Asian markets
- **Commodity Markets**: Oil, Gold, Silver, Agricultural products analysis
- **Forex Markets**: Major currency pairs and cross-currency analysis

### Asset Diversification

- **Fixed Income**: Government bonds, corporate bonds, and yield analysis agents
- **Derivatives**: Options, futures, and complex financial instruments
- **Alternative Investments**: Private equity, hedge funds, and venture capital analysis

### Advanced Notification & Push Types

- **Real-time Alerts**: Price movements, volume spikes, and technical breakouts
- **Scheduled Reports**: Daily/weekly/monthly portfolio summaries
- **Event-driven Notifications**: Earnings releases, dividend announcements, regulatory changes
- **Custom Triggers**: User-defined conditions and thresholds
- **Multi-channel Delivery**: Email, SMS, Slack, Discord, and webhook integrations

## ⚙️ Product Configuration & Personalization

### Internationalization (i18n)

- **Multi-language Support**: English, Chinese (Simplified/Traditional), Japanese, Korean, Spanish, French
- **Localized Market Data**: Region-specific financial terminology and formats
- **Cultural Adaptation**: Time zones, date formats, and currency preferences
- **Agent Personality Localization**: Culturally appropriate communication styles

### Token & Authentication Management

- **API Key Management**: Secure storage and rotation of third-party API keys
- **OAuth Integration**: Support for major financial data providers
- **Rate Limiting**: Intelligent request throttling and quota management
- **Multi-tenant Architecture**: Enterprise-grade user isolation and security

### User Preferences & Customization

- **Investment Profile**: Risk tolerance, investment horizon, and strategy preferences
- **UI/UX Customization**: Dark/light mode, dashboard layouts, and widget preferences
- **Agent Behavior**: Communication frequency, analysis depth, and reporting style
- **Portfolio Management**: Custom benchmarks, performance metrics, and allocation targets

### Memory & Learning Systems

- **Conversation History**: Persistent chat history across sessions
- **User Learning**: Adaptive recommendations based on user behavior
- **Market Memory**: Historical context and pattern recognition
- **Preference Evolution**: Dynamic adjustment of recommendations over time

## 🔧 ValueCell SDK Development

### Core SDK Features

- **Python SDK**: Comprehensive library for agent integration and customization
- **REST API Wrapper**: Simplified HTTP client with automatic authentication
- **WebSocket Support**: Real-time data streaming and bidirectional communication

### Agent Integration Framework

- **Plugin Architecture**: Easy integration of third-party agents and tools
- **Agent Registry**: Marketplace for community-contributed agents
- **Custom Agent Builder**: Low-code/no-code agent creation tools
- **Agent Orchestration**: Workflow management and agent coordination

### Developer Tools & Documentation

- **Interactive API Explorer**: Swagger/OpenAPI documentation with live testing
- **Code Examples**: Sample implementations in multiple programming languages
- **Testing Framework**: Unit tests, integration tests, and mock data providers

# Star History

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
