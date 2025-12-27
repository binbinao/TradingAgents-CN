# TradingAgents 项目详细规格说明书 (Spec)

> 作者：PyMaster AI导师  
> 更新时间：2025-12-27  
> 目标：帮助开发者快速理解项目结构与运行机制

---

## 1️⃣ 项目概述

**项目名称**：TradingAgents  
**定位**：基于多智能体（Multi-Agent）架构的股票分析与自动化交易系统，融合数据分析、新闻情感过滤、LLM 推理与可视化前端。  
**核心特色**：
- 多数据源支持（AKShare、Baostock、Tushare）
- 多智能体协作（研究员、分析师、交易员、风控）
- LLM 驱动的决策与报告生成（支持多种大模型 API）
- 前后端分离 + Docker 一键部署
- 丰富的数据预处理与缓存机制

---

## 2️⃣ 目录结构说明

```
TradingAgents-CN/
├── app/                 # 主应用后端逻辑
│   ├── __init__.py
│   ├── __main__.py      # 应用入口
│   ├── main.py          # FastAPI 路由与业务逻辑
│   ├── worker.py        # 后台任务处理
│   └── LICENSE
├── assets/              # 静态图片资源（角色头像、Logo）
├── cli/                 # 命令行工具集
│   ├── akshare_init.py  # AKShare 数据初始化
│   ├── baostock_init.py
│   ├── tushare_init.py
│   ├── main.py          # CLI 主入口
│   ├── models.py
│   └── utils.py
├── config/              # 配置文件
│   ├── logging.toml
│   ├── logging_docker.toml
│   └── README.md
├── data/                # 数据与文档
├── docker/              # Nginx 配置
├── docker-compose.yml   # 容器编排
├── Dockerfile.backend   # 后端镜像构建
├── Dockerfile.frontend  # 前端镜像构建
├── docs/                # 详细文档（构建、配置、故障排查）
├── examples/            # 示例代码与演示脚本
├── frontend/            # Vue3 + Vite 前端项目
├── images/              # 额外图片
├── install/             # 安装相关配置
├── nginx/               # Nginx 生产配置
├── reports/             # 日志与修复报告
├── scripts/             # 各类辅助脚本（数据检查、同步、构建）
├── tests/               # 单元测试与集成测试
├── tradingagents/       # 核心业务代码包
├── utils/               # 通用工具函数
├── pyproject.toml       # 项目依赖与构建配置
├── requirements.txt     # 依赖列表
├── README.md            # 项目简介
└── _mydocs/spec.md      # 本规格说明书
```

---

## 3️⃣ 核心模块与职责

| 模块 | 路径 | 主要职责 |
|------|------|----------|
| **后端 API** | `app/` | FastAPI 提供 RESTful 接口，调度多智能体任务 |
| **CLI 工具** | `cli/` | 数据初始化、批量导入、快速测试 |
| **前端界面** | `frontend/` | Vue3 可视化交互，展示分析结果、执行交易模拟 |
| **核心逻辑** | `tradingagents/` | 智能体定义、LLM 调用、决策流程 |
| **数据脚本** | `scripts/` | 数据抓取、校验、同步、统计 |
| **配置管理** | `config/` | 日志、运行时参数 |
| **文档中心** | `docs/` | 安装、部署、故障排查指南 |
| **示例入口** | `examples/` | 快速体验各功能的 Demo |

---

## 4️⃣ 技术栈

- **后端**：Python 3.11+, FastAPI, Pydantic, SQLAlchemy, MongoDB, Redis
- **前端**：Vue 3, Vite, TypeScript, Pinia, Axios
- **数据源**：AKShare, Baostock, Tushare
- **LLM 支持**：OpenAI, DeepSeek, Google Gemini, SiliconFlow, 302.AI 等
- **容器化**：Docker, Docker Compose, Nginx
- **任务队列**：Celery / FastAPI BackgroundTasks
- **测试**：pytest
- **代码规范**：Black, ESLint, Prettier

---

## 5️⃣ 运行与部署

### 本地开发
1. 创建虚拟环境：`uv venv -p 3.11 && source .venv/bin/activate`
2. 安装依赖：`pip install -r requirements.txt`
3. 启动后端：`uvicorn app.main:app --reload`
4. 启动前端：`cd frontend && yarn dev`

### Docker 部署
```bash
# 一键启动全部服务
 docker-compose up --build
```
- 后端服务映射至 `localhost:8000`
- 前端服务映射至 `localhost:5173`（Vite 默认）
- Nginx 作为反向代理与静态资源服务

---

## 6️⃣ 其他关键信息

- **许可证**：详见 `LICENSE`、`COPYRIGHT.md`
- **贡献指南**：`CONTRIBUTORS.md`、`docs/BUILD_GUIDE.md`
- **API Key 管理**：`docs/API_KEY_MANAGEMENT_ANALYSIS.md`
- **多架构 Docker 构建**：`docs/docker-multiarch-build.md`
- **常见问题**：`docs/troubleshooting-mongodb-docker.md`

---

## 7️⃣ 核心要点总结

1. **TradingAgents** 是多智能体股票分析+交易系统，覆盖数据→分析→决策→可视化全流程。
2. 项目结构清晰，分为后端、前端、CLI、脚本、文档五大板块。
3. 技术栈现代化，支持 Docker 一键部署与多 LLM 接入。
4. 通过 `_mydocs/spec.md` 可快速掌握项目全貌，降低上手成本。

---

✅ **PyMaster提示**：这份 Spec 可作为团队 onboarding 与项目维护的“地图”，建议放在仓库显眼位置并随项目迭代更新。  
如需进一步细化某个模块的流程图或类图，可告诉我，我帮你画 Mermaid 图！🚀