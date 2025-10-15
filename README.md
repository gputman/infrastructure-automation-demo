# Infrastructure Automation Demo

This repository demonstrates a **simple DevOps automation workflow** using **PowerShell**, **REST API calls**, and **GitHub Actions**. It’s intentionally lightweight so recruiters can quickly see working code, a CI pipeline, and clean version-control practices.

## What this shows

- PowerShell scripting with parameters and error handling
- `Invoke-RestMethod` to call REST endpoints and parse JSON
- CI pass/fail gate in GitHub Actions (runs on every push and PR)
- Mock-first pattern (works without secrets or external dependencies)
- Optional real endpoint override for local testing

## Repo structure

```
infrastructure-automation-demo/
├─ scripts/
│  ├─ Get-ServerHealth.ps1
│  └─ Restart-VM.ps1
├─ data/
│  └─ health.json
├─ .github/
│  └─ workflows/
│     └─ github-actions.yml
└─ README.md
```

## Quick start

1. **Clone** the repo:
   ```bash
   git clone https://github.com/gputman/infrastructure-automation-demo
   cd infrastructure-automation-demo
   ```

2. **Run with mock data** (no secrets needed):
   ```bash
   pwsh ./scripts/Get-ServerHealth.ps1
   ```

3. **(Optional) Run against a public REST endpoint**:
   ```bash
   pwsh ./scripts/Get-ServerHealth.ps1 -EndpointUrl "https://api.github.com/rate_limit"
   ```
   Other examples:
   - `https://worldtimeapi.org/api/timezone/America/Phoenix`
   - `https://jsonplaceholder.typicode.com/todos/1`

4. **Branch & Pull Request (to demonstrate collaboration)**:
   ```bash
   git checkout -b feature/update-health-threshold
   # make a small change, commit, push
   git push -u origin feature/update-health-threshold
   # open a PR in GitHub
   ```

## CI workflow

GitHub Actions workflow: `.github/workflows/github-actions.yml`

- Installs PowerShell on `ubuntu-latest`
- Runs the health script with mock data to keep CI green
- Exits non-zero if the mock indicates a failure condition

## Security note

- No secrets are required for the default CI path.
- If you later integrate real endpoints (e.g., OneView/Dynatrace), use **repository secrets** and environment variables.
- The script supports a `-BearerToken` parameter for authenticated APIs; pass it via environment secret in Actions if needed.

## Skills demonstrated

- PowerShell automation
- REST/JSON parsing with `Invoke-RestMethod`
- GitHub branching, PRs, code review readiness
- CI/CD concepts and pass/fail quality gates
- Infrastructure-minded patterns (mock-first, parameters, safe defaults)

---

> *Created by Gregory Putman — Infrastructure & DevOps Engineer*  
> LinkedIn: https://www.linkedin.com/in/gregory-putman-4686034  
> GitHub:  https://github.com/gputman
