# TradingAgents-CN Project Documentation

## Project Overview

TradingAgents-CN is a Chinese-enhanced multi-agent trading framework based on large language models (LLMs). It extends the original [TradingAgents](https://github.com/TauricResearch/TradingAgents) project with specialized features for Chinese markets, including:

- 🧠 Multi-agent architecture for financial analysis
- 🇨🇳 Native support for A-shares, H-shares, and US stocks
- 🤖 Integration with multiple LLM providers (DashScope, DeepSeek, Google AI)
- 📊 Comprehensive financial data processing pipeline
- 🐳 Docker-based deployment

## Key Technologies

- **Core Language**: Python 3.10+
- **Frameworks**:
  - LangChain for agent orchestration
  - Streamlit for web interface
- **Data Sources**:
  - Tushare
  - AkShare
  - FinnHub
  - Yahoo Finance
- **Database**:
  - MongoDB for persistent storage
  - Redis for caching

## Project Structure

```
TradingAgents-CN/
├── .env.example          # Environment template
├── docker-compose.yml    # Docker configuration
├── Dockerfile            # Container setup
├── main.py               # Main entry point
├── pyproject.toml        # Python project config
├── requirements.txt      # Python dependencies
├── tradingagents/        # Core application
│   ├── agents/           # Analyst agents
│   ├── data/             # Data processing
│   ├── llm_providers/    # LLM integrations
│   └── utils/            # Utility functions
├── web/                  # Streamlit UI
├── scripts/              # Utility scripts
├── config/               # Configuration files
├── data/                 # Data storage
├── logs/                 # Application logs
└── docs/                 # Documentation
```

## Building and Running

### Docker Deployment (Recommended)

```bash
# 1. Clone the repository
git clone https://github.com/hsliuping/TradingAgents-CN.git
cd TradingAgents-CN

# 2. Configure environment
cp .env.example .env
# Edit .env with your API keys

# 3. Start services
docker-compose up -d --build

# Access:
# Web UI: http://localhost:8501
# MongoDB Admin: http://localhost:8082
# Redis Admin: http://localhost:8081
```

### Local Development

```bash
# 1. Setup environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# 2. Install dependencies
pip install -e .

# 3. Start application
python start_web.py
```

## Development Conventions

1. **Code Style**:
   - PEP 8 compliance
   - Type hints for all public methods
   - Google-style docstrings

2. **Testing**:
   - Unit tests in `tests/` directory
   - Mock external API calls
   - Integration tests for core workflows

3. **Documentation**:
   - Keep `docs/` updated
   - Document new features in CHANGELOG.md
   - Maintain API documentation

4. **Branching**:
   - `main` for production-ready code
   - `feature/*` for new features
   - `bugfix/*` for bug fixes

## Key Configuration Files

| File | Purpose |
|------|---------|
| `.env` | Environment variables |
| `pyproject.toml` | Python project config |
| `docker-compose.yml` | Docker services |
| `config/*.yaml` | Application configs |

## Data Flow

1. User Input → Web Interface
2. → Agent Orchestrator
3. → Data Processing Pipeline
   - Cache Check (Redis)
   - API Fallback
4. → LLM Processing
5. → Result Aggregation
6. → Report Generation

## Contribution Guidelines

1. Fork the repository
2. Create feature branches (`feature/your-feature`)
3. Submit PRs with:
   - Clear description
   - Tests
   - Documentation updates

See [CONTRIBUTORS.md](CONTRIBUTORS.md) for details.