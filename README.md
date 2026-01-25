# Custom Private Agent

A private, optimized multi-agent development system with local model support, specialized developer profiles, and MCP integration.

## Features

- ✅ **Private Local Models** - Full privacy with Ollama integration (llama3.2, nomic-embed-text)
- ✅ **Specialized Developer Profiles** - 6 profiles: Senior Developer, Full-Stack, ML Engineer, DevOps, Security, Data Engineer
- ✅ **MCP Server** - 7 tools for development workflows (code generation, review, architecture, testing, documentation)
- ✅ **Task Management** - Priority-based task queue with lifecycle management
- ✅ **Multi-Agent Coordination** - Automated task distribution among specialized agents
- ✅ **Developer Optimizations** - Code review automation, test generation, security analysis

## Quick Start

### Prerequisites
- Docker
- 8GB+ RAM (16GB recommended for local models)
- Windows, Linux, or macOS

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/B0LK13/custom-private-agent.git
   cd custom-private-agent
   ```

2. **Start containers (Docker Compose)**
   ```bash
   docker-compose up -d
   ```

3. **Access the UI**
   - Open: `http://localhost:50001`
   - Default login configured automatically

## Configuration

### Environment Variables

**Essential Settings:**
```env
# Primary provider (change to 'ollama' for local models)
MODEL_PROVIDER=default
MODEL_AUTO=default

# OpenAI (if using cloud models)
OPENAI_API_KEY=sk-
OPENAI_API_BASE=https://api.openai.com/v1
MODEL_OPENAI=gpt-4o

# Local Ollama Models
PRIMARY_MODEL_PROVIDER=ollama
MODEL_NAME=llama3.2
OLLAMA_ENABLED=true
OLLAMA_HOST=http://ollama:11434
OLLAMA_EMBEDDING_MODEL=nomic-embed-text
```

### Developer Profile Selection
```env
PRIMARY_PROFILE=senior_developer
```

Available profiles:
- `senior_developer` - Production-ready coding
- `fullstack_developer` - React/Node.js web apps
- `ml_engineer` - ML/AI systems
- `devops_sre` - Infrastructure & DevOps
- `security_engineer` - Security & compliance
- `data_engineer` - Data pipelines

## Developer Optimizations

### Code Features
- **Auto Code Review** - Review for bugs, security, performance
- **Auto Test Generation** - Unit, integration, E2E tests
- **Auto Documentation** - Markdown, Javadoc, docstrings
- **Linting Auto-fix** - Automated code style fixes

### Performance Features
- **Rate Limiting** - Configurable request limits
- **Response Caching** - Reduces redundant API calls
- **Parallel Execution** - Multi-tool concurrent execution
- **Task Prioritization** - Critical tasks first

### Quality Features
- **Security Analysis** - OWASP compliance, dependency scanning
- **Performance Monitoring** - Bottleneck detection
- **Thinking & Reasoning** - Deep chain-of-thought capabilities

## MCP Server Integration

### Windurf IDE Configuration

**Location:** `C:\Users\Admin\.codeium\windsurf\mcp_config.json`

**Available Tools:**
```
@agentx code-generation      # Generate code with profiles
@agentx code-review          # Review code for issues
@agentx architecture-design  # System design
@agentx generate-tests      # Create tests
@agentx documentation       # Generate docs
@agentx profile-list        # List profiles
@agentx profile-get         # Get profile details
```

**Example Usage (in Winds Cascade):**
```
@agentx Create a REST API for user authentication
@agentx --profile senior_developer
@agentx --language rust
```

## Local Models (Full Privacy)

### Supported Models
- **llama3.2** - Main chat model (4GB, 128k context)
- **nomic-embed-text** - Embeddings for RAG (200MB)
- **mistral** - Faster alternative (2GB)
- **codellama** - Code-optimized (4GB)

### Configuration
```env
PRIMARY_MODEL_PROVIDER=ollama
MODEL_NAME=llama3.2
OLLAMA_HOST=http://localhost:11434
OLLAMA_CHAT_MODEL=llama3.2
OLLAMA_EMBEDDING_MODEL=nomic-embed-text
```

### Benefits
- **100% Privacy** No data leaves your system
- **No Cost** No per-token charges
- **Offline Works** Without internet connection
- **Full Control** Choose models and versions

## Project Structure

```
custom-private-agent/
├── src/
│   ├── profiles/          # Developer profiles (6 profiles)
│   ├── task-management/   # Task priority system
│   ├── mcp-server/        # MCP server (7 tools)
│   └── config/            # Configuration files
├── docs/                  # Documentation
│   ├── 001-config-fix-404-errors.md
│   ├── 002-developer-profiles.md
│   ├── 003-mcp-server.md
│   ├── 004-task-management-system.md
│   ├── 005-private-local-models.md
│   └── 006-complete-change-summary.md
└── README.md
```

## Access Points

| Service | URL | Port |
|---------|-----|------|
| Agent Zero UI | http://localhost | 50001 |
| Ollama API | http://localhost | 11434 |
| SSH | - | 50022 |

## Quick Commands

### Check Status
```bash
# Container status
docker ps | grep agent

# Health check
curl -s http://localhost:50001/health

# Ollama models
docker exec agent-zero-ollama ollama list
```

### Pull Models
```bash
docker exec agent-zero-ollama ollama pull llama3.2
docker exec agent-zero-ollama ollama pull nomic-embed-text
```

### Restart Services
```bash
docker restart agent-zero-advanced
docker restart agent-zero-ollama
```

## Documentation

- [Config Fix (404 Errors)](docs/001-config-fix-404-errors.md)
- [Developer Profiles](docs/002-developer-profiles.md)
- [MCP Server](docs/003-mcp-server.md)
- [Task Management](docs/004-task-management-system.md)
- [Local Models](docs/005-private-local-models.md)
- [Complete Summary](docs/006-complete-change-summary.md)

## Requirements

- **Minimum:** 8GB RAM, Docker
- **Recommended:** 16GB RAM, 8 or more CPU cores
- **GPU:** Optional (for faster local inference)

## Troubleshooting

### 404 Errors
Ensure `OPENAI_API_BASE` is set to `https://api.openai.com/v1`

### Local Models Not Working
Check Ollama models are installed and OLLAMA_HOST points to `http://ollama:11434`

### MCP Tools Not Available
Restart Windsurf after configuration changes

## Status

- ✅ Agent Zero configured and running
- ✅ Ollama local models installed
- ✅ Developer profiles implemented
- ✅ MCP server created (binary pending)
- ✅ Task management system ready
- ✅ Documentation complete

## Support

For issues, check:
1. Container logs: `docker logs <container>`
2. Configuration: Verify `.env` settings
3. Troubleshooting docs in `/docs` folder

## License

MIT License