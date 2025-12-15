# Tupinamba Energia - Organization Defaults

Organization-wide GitHub configurations and workflow templates.

## Workflow Templates

### Claude Code Review

Automated PR code review using Claude AI with specialized engineering agents from [tupi-ai](https://github.com/tupinamba-energia/tupi-ai).

#### Setup

1. **Add the workflow** - Go to Actions > New workflow > find "Claude Code Review"
2. **Set up secret** - Ensure `ANTHROPIC_API_KEY` is configured in repo or org secrets

That's it. The workflow automatically installs the tupi-ai plugin at runtime.

#### Available Agents

| Agent | Focus |
|-------|-------|
| `security-auditor` | OWASP, vulnerabilities, auth |
| `performance-optimizer` | Bottlenecks, caching, optimization |
| `debugger-expert` | Bug detection, root cause analysis |
| `typescript-guardian` | TypeScript type safety |
| `javascript-architect` | Modern JS, async patterns |
| `python-mentor` | Python 3.12+, FastAPI |
| `elixir-master` | OTP, Phoenix, BEAM |
| `ai-alchemist` | LLM apps, RAG systems |
| `observability-specialist` | Monitoring, SLI/SLO |
| `devops-troubleshooter` | Infrastructure, K8s, CI/CD |
