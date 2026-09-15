# Tupinamba Energia - Organization Defaults

Organization-wide GitHub configurations and workflow templates.

## Workflow Templates

### Asana PR Sync

Liga o ciclo de vida do PR ao card no board [Scrumban · Engenharia](https://app.asana.com/1/1207415061784768/project/1217376162375967) no Asana.

| Evento no GitHub | Efeito |
|---|---|
| PR aberto | forcado para draft; exige a URL da task no corpo; card sai de `Backlog`/`Ready to Dev` para `WIP` |
| ready for review sem reviewer | volta para draft, com o motivo em comentario |
| ready for review com reviewer | card para `Review / PR`, campo `Reviewer` preenchido, subtask por reviewer |
| review submetido | comentario no card |
| PR fechado | subtasks do PR completadas; sem merge volta para `WIP`; com merge e sem outro PR aberto vai para `DEV QA` |

Card em `Blocked` nunca e movido: a automacao comenta o destino pretendido e deixa a decisao com quem bloqueou.

#### Setup

1. **Adicione o workflow** - Actions > New workflow > "Asana PR Sync"
2. **Secrets** - `ASANA_PAT` (token de service account do Asana) e `ASANA_USER_MAP`
   (JSON `{"login-github": "gid-asana"}`) na org ou no repo
3. **Ruleset** (opcional) - marque `asana / asana-gate` como required status check.
   Confirme o nome exato do check num PR antes, senao trava o merge do repo.

A logica fica em `.github/workflows/asana-pr-sync.yml`, chamado como reusable workflow.
Os GIDs do board sao defaults desse arquivo, entao o caller de cada repo nao tem configuracao.

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
