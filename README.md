# DevOps & DataOps — Site + CI/CD (GitHub Pages)

Entrega acadêmica em **uma página HTML** com resumo de DevOps & DataOps (CALMS, SDLC, Shift Left, CI/CD e runbooks), publicada automaticamente no **GitHub Pages** usando **GitHub Actions**.

## Estrutura

```text
.
├── site/
│   └── index.html
└── .github/
    └── workflows/
        ├── ci.yml
        └── cd.yml
```

## Como funciona

- **CI** (`.github/workflows/ci.yml`)
  - Dispara em mudanças em `site/**`
  - Valida que `site/index.html` existe
  - Faz checagens básicas (DOCTYPE, title, main, fechamento do HTML)

- **CD** (`.github/workflows/cd.yml`)
  - Dispara em `push` na branch `main` (quando muda `site/**`)
  - Faz upload **somente** da pasta `site/`
  - Publica no GitHub Pages

## Publicação (GitHub Pages)

No GitHub, configure:

1. **Settings → Pages**
2. Em **Build and deployment**, selecione **Source: GitHub Actions**
3. Faça um push na `main` e acompanhe em **Actions**

URL esperada (após o primeiro deploy):

- `https://magnasoluto.github.io/DataOps/`

## Referências

- IBM — DevOps: `https://www.ibm.com/br-pt/think/topics/devops`
- Atlassian — Runbook template: `https://www.atlassian.com/br/software/confluence/templates/devops-runbook`
- Microsoft Learn — Managed Identity troubleshooting: `https://learn.microsoft.com/pt-br/azure/automation/troubleshoot/managed-identity`
- GitHub Actions Docs: `https://docs.github.com/pt/actions`

