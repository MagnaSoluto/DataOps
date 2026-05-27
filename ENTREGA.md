# Entrega — DevOps & DataOps (CI/CD + GitHub Pages)

**Aluno:** Adriano Carvalho dos Santos  
**RA:** 10747203  
**Disciplina:** DevOps & DataOps  
**Professora:** Debora Batista Paulo  

## 1) Objetivo

Construir um projeto simples com **uma página HTML** e automatizar um pipeline **CI/CD** com **GitHub Actions**, publicando a página no **GitHub Pages**, conforme a atividade prática de “Pipeline Automatizado CI/CD”.

## 2) Repositório e site publicado

- **Repositório:** `git@github.com:MagnaSoluto/DataOps.git`
- **URL do GitHub Pages:** `https://magnasoluto.github.io/DataOps/`

## 3) Estrutura do projeto

```text
.
├── site/
│   └── index.html
└── .github/
    └── workflows/
        ├── ci.yml
        └── cd.yml
```

## 4) Conteúdo da página (resumo)

A página `site/index.html` condensa os principais tópicos vistos em aula, incluindo:

- Evolução do desenvolvimento: **Waterfall → Ágil → DevOps → DataOps**
- Pilares **CALMS** (Culture, Automation, Lean, Measurement, Sharing)
- **SDLC** e ciclo de vida DevOps
- **Shift Left** e tipos de testes
- Conceitos de **CI / CD / Pipeline** e comparação DevOps vs DataOps
- **Runbook** prático (sintoma, impacto, causas, passo a passo e escalonamento)
- Seção de **referências** com links de documentação sugeridos

## 5) CI (Integração Contínua) — `.github/workflows/ci.yml`

**Quando executa**

- Em todo `push` que altera `site/**`
- Também pode ser executado manualmente (`workflow_dispatch`)

**O que valida**

- Verifica se existe `site/index.html`
- Checagens leves de consistência do HTML:
  - `<!doctype html`
  - `<title>`
  - `</html>`
  - `<main`

**Como evidenciar**

- Acesse **Actions** → workflow **“CI - Validar site HTML”** → veja o log da execução verde.

## 6) CD (Deploy Contínuo) — `.github/workflows/cd.yml`

**Quando executa**

- Em `push` na branch `main` com mudanças em `site/**`
- Também pode ser executado manualmente (`workflow_dispatch`)

**O que faz**

- Configura o GitHub Pages (com `enablement: true` para habilitar/criar Pages se necessário)
- Faz upload **somente** da pasta `site/`
- Publica no **GitHub Pages**

**Como evidenciar**

- Acesse **Actions** → workflow **“CD - Deploy para GitHub Pages”** → veja a execução verde.
- Abra a URL do Pages e capture um print da página publicada (opcional).

## 7) Como gerar o “arquivo do trabalho” para entregar (PDF)

Se a professora pedir um **arquivo** (PDF), a forma mais simples é gerar um PDF desta documentação e/ou do site:

### Opção A — Gerar PDF do `ENTREGA.md`
1. Abra `ENTREGA.md` no GitHub (ou no VSCode/Cursor)
2. Use **Imprimir** (Ctrl/Cmd + P)
3. Escolha **Salvar como PDF**

### Opção B — Gerar PDF do site publicado
1. Abra `https://magnasoluto.github.io/DataOps/`
2. Ctrl/Cmd + P → **Salvar como PDF**

## 8) Referências (links fornecidos)

- IBM — DevOps: `https://www.ibm.com/br-pt/think/topics/devops`
- Atlassian — Runbook template: `https://www.atlassian.com/br/software/confluence/templates/devops-runbook`
- Microsoft Learn — Managed Identity troubleshooting: `https://learn.microsoft.com/pt-br/azure/automation/troubleshoot/managed-identity`
- GitHub Actions Docs: `https://docs.github.com/pt/actions`

