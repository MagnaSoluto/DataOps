<div align="center">

# DevOps & DataOps — Pipeline CI/CD + GitHub Pages

**Atividade prática · Pipeline Automatizado CI/CD**

<br/>

![CI](https://img.shields.io/github/actions/workflow/status/MagnaSoluto/DataOps/ci.yml?branch=main&label=CI&style=for-the-badge&logo=githubactions&logoColor=white)
![CD](https://img.shields.io/github/actions/workflow/status/MagnaSoluto/DataOps/cd.yml?branch=main&label=CD&style=for-the-badge&logo=githubpages&logoColor=white)
![GitHub Pages](https://img.shields.io/website?url=https%3A%2F%2Fmagnasoluto.github.io%2FDataOps%2F&style=for-the-badge&label=Pages&up_message=online&down_message=offline)
![HTML5](https://img.shields.io/badge/site-index.html-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/Automação-GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)

<br/>

![Aluno](https://img.shields.io/badge/Aluno-Adriano_Carvalho_dos_Santos-0A192F?style=flat-square)
![RA](https://img.shields.io/badge/RA-10747203-007ACC?style=flat-square)
![Disciplina](https://img.shields.io/badge/Disciplina-DevOps_%26_DataOps-6C63FF?style=flat-square)
![Professora](https://img.shields.io/badge/Prof%C2%AA-Debora_Batista_Paulo-C2185B?style=flat-square)

<br/>

**Site publicado:** [magnasoluto.github.io/DataOps](https://magnasoluto.github.io/DataOps/)  
**Repositório:** [github.com/MagnaSoluto/DataOps](https://github.com/MagnaSoluto/DataOps)

</div>

---

## Visão geral

Entrega individual com **uma página HTML moderna** condensando a matéria de **DevOps & DataOps**, publicada automaticamente via **GitHub Actions** no **GitHub Pages**.

| Item | Detalhe |
|------|---------|
| **Objetivo** | Criar, configurar e validar um pipeline CI/CD completo |
| **Stack** | Git · GitHub · GitHub Actions · GitHub Pages · HTML/CSS |
| **Branch** | `main` |
| **Deploy** | Automático a cada push em `site/**` |

---

## Pipeline (fluxo automatizado)

```mermaid
flowchart LR
  A[Push na main] --> B[CI validar HTML]
  B --> C{Passou?}
  C -->|Sim| D[CD deploy Pages]
  C -->|Não| E[Falha no log]
  D --> F[Site online]
```

```
  ┌─────────────┐     ┌──────────────────┐     ┌─────────────────────┐     ┌──────────────────┐
  │ git push    │ ──► │  CI · ci.yml     │ ──► │  CD · cd.yml        │ ──► │  GitHub Pages    │
  │  site/**    │     │  validar HTML    │     │  upload site/       │     │  /DataOps/       │
  └─────────────┘     └──────────────────┘     └─────────────────────┘     └──────────────────┘
```

---

## Estrutura do repositório

```text
DataOps/
├── site/
│   └── index.html              ← Página única da entrega
└── .github/
    └── workflows/
        ├── ci.yml              ← Integração Contínua
        └── cd.yml              ← Deploy Contínuo (Pages)
```

---

## Conteúdo do site (`site/index.html`)

| Seção | Tópicos |
|-------|---------|
| **Fundamentos** | Waterfall → Ágil → DevOps → DataOps |
| **CALMS** | Culture · Automation · Lean · Measurement · Sharing |
| **SDLC** | 7 fases + ciclo DevOps (8 etapas) |
| **Shift Left** | Testes antecipados · unidade · integração · API |
| **CI/CD** | Pipeline · fluxo commit → deploy · DevOps vs DataOps |
| **Runbook** | API 500 · causas · 5 passos · escalonamento |
| **Referências** | IBM · Atlassian · Microsoft · GitHub Actions |

---

## Workflows

### CI — Integração Contínua

![Workflow CI](https://img.shields.io/github/actions/workflow/status/MagnaSoluto/DataOps/ci.yml?branch=main&label=ci.yml&style=flat-square&logo=githubactions)
![Trigger](https://img.shields.io/badge/trigger-push%20em%20site%2F**-blue?style=flat-square)
![Runner](https://img.shields.io/badge/runner-ubuntu--latest-333?style=flat-square&logo=ubuntu&logoColor=white)

| Etapa | Descrição |
|-------|-----------|
| **Checkout** | Clona o repositório |
| **Validar** | Confirma existência de `site/index.html` |
| **Checar HTML** | DOCTYPE · `<title>` · `<main>` · `</html>` |
| **Notificar** | Job secundário após CI verde |

<details>
<summary><strong>Simulação · log do CI (GitHub Actions)</strong></summary>

<br/>

```text
┌─ CI - Validar site HTML ────────────────────────────────────────────────┐
│  Run #N · push · main · MagnaSoluto/DataOps                             │
├─────────────────────────────────────────────────────────────────────────┤
│  ✓  Set up job                                              1s          │
│  ✓  Clonar repositório                                      1s          │
│  ✓  Verificar se existe site/index.html                     0s          │
│      → Arquivo encontrado com sucesso!                                  │
│  ✓  Checagens leves de consistência do HTML                 0s          │
│      → Checagens básicas OK.                                            │
├─────────────────────────────────────────────────────────────────────────┤
│  ✓  notificar · Evento disparado                            0s          │
│      → Alteração em site/** detectada e validada com sucesso!           │
└─────────────────────────────────────────────────────────────────────────┘
  Status:  passing   ·   Duração: ~14s
```

</details>

---

### CD — Deploy Contínuo

![Workflow CD](https://img.shields.io/github/actions/workflow/status/MagnaSoluto/DataOps/cd.yml?branch=main&label=cd.yml&style=flat-square&logo=githubpages)
![Trigger](https://img.shields.io/badge/trigger-push%20main%20+%20site%2F**-blue?style=flat-square)
![Artifact](https://img.shields.io/badge/artifact-site%2F-green?style=flat-square)

| Etapa | Descrição |
|-------|-----------|
| **Configure Pages** | Habilita Pages (`enablement: true`) |
| **Upload artifact** | Envia **somente** a pasta `site/` |
| **Deploy Pages** | Publica em `github-pages` environment |

<details>
<summary><strong>Simulação · log do CD (GitHub Actions)</strong></summary>

<br/>

```text
┌─ CD - Deploy para GitHub Pages ─────────────────────────────────────────┐
│  Run #N · push · main · MagnaSoluto/DataOps                             │
├─────────────────────────────────────────────────────────────────────────┤
│  ✓  Set up job                                              1s          │
│  ✓  Clonar repositório                                      1s          │
│  ✓  Configurar GitHub Pages                                 2s          │
│  ✓  Fazer upload do site                                    1s          │
│      → path: site/                                                      │
│  ✓  Publicar no GitHub Pages                               15s          │
│      → Deployed to github-pages environment                             │
└─────────────────────────────────────────────────────────────────────────┘
  Status:  passing   ·   Duração: ~22s
  URL:     https://magnasoluto.github.io/DataOps/
```

</details>

---

## Evidências da entrega

<div align="center">

### GitHub Actions — execuções

[![Actions](https://img.shields.io/badge/Ver_todos_os_workflows-Actions-2088FF?style=for-the-badge&logo=github&logoColor=white)](https://github.com/MagnaSoluto/DataOps/actions)

</div>

<br/>

| Status | Workflow | Branch | Resultado |
|:------:|----------|:------:|:---------:|
| ![passing](https://img.shields.io/badge/status-passing-brightgreen?style=flat-square) | **CI - Validar site HTML** | `main` | Validação OK |
| ![passing](https://img.shields.io/badge/status-passing-brightgreen?style=flat-square) | **CD - Deploy para GitHub Pages** | `main` | Deploy OK |

<br/>

<details open>
<summary><strong>Simulação · tela Actions (GitHub)</strong></summary>

<br/>

```text
  Actions  ›  All workflows
  ─────────────────────────────────────────────────────────────────────

  ●  Fix: habilitar Pages no deploy          CD - Deploy para GitHub Pages #2
     main · 601e0aa · MagnaSoluto              ✓  22s

  ●  Site DevOps & DataOps com CI/CD         CI - Validar site HTML #1
     main · bec87a6 · MagnaSoluto              ✓  14s

  ●  Site DevOps & DataOps com CI/CD         CD - Deploy para GitHub Pages #1
     main · bec87a6 · MagnaSoluto              ✗  8s   ← corrigido no #2
```

</details>

<br/>

### Checklist final

| Evidência | Status |
|-----------|:------:|
| Site publicado em [magnasoluto.github.io/DataOps](https://magnasoluto.github.io/DataOps/) | ![ok](https://img.shields.io/badge/✓-online-brightgreen?style=flat-square) |
| Workflow **CI** executado com sucesso | ![ok](https://img.shields.io/badge/✓-passing-brightgreen?style=flat-square) |
| Workflow **CD** executado com sucesso | ![ok](https://img.shields.io/badge/✓-passing-brightgreen?style=flat-square) |
| Pages com **Source: GitHub Actions** | ![ok](https://img.shields.io/badge/✓-configurado-brightgreen?style=flat-square) |

<br/>

### Artefatos entregues

![index.html](https://img.shields.io/badge/site-index.html-entregue-success?style=flat-square&logo=html5)
![ci.yml](https://img.shields.io/badge/.github-ci.yml-entregue-success?style=flat-square&logo=githubactions)
![cd.yml](https://img.shields.io/badge/.github-cd.yml-entregue-success?style=flat-square&logo=githubpages)
![readme](https://img.shields.io/badge/README.md-entregue-success?style=flat-square&logo=markdown)

---

## Configuração GitHub Pages

| Passo | Ação |
|:-----:|------|
| 1 | **Settings → Pages** |
| 2 | **Build and deployment → Source:** `GitHub Actions` |
| 3 | Push na `main` dispara CI + CD automaticamente |

![Pages Source](https://img.shields.io/badge/Source-GitHub_Actions-2088FF?style=for-the-badge&logo=github&logoColor=white)
![Environment](https://img.shields.io/badge/environment-github--pages-purple?style=for-the-badge)

---

## Referências

<div align="center">

[![IBM DevOps](https://img.shields.io/badge/IBM-O_que_é_DevOps?-054ADA?style=for-the-badge&logo=ibm&logoColor=white)](https://www.ibm.com/br-pt/think/topics/devops)
[![Atlassian Runbook](https://img.shields.io/badge/Atlassian-Template_Runbook-0052CC?style=for-the-badge&logo=atlassian&logoColor=white)](https://www.atlassian.com/br/software/confluence/templates/devops-runbook)
[![Microsoft Learn](https://img.shields.io/badge/Microsoft-Managed_Identity-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)](https://learn.microsoft.com/pt-br/azure/automation/troubleshoot/managed-identity)
[![GitHub Actions Docs](https://img.shields.io/badge/GitHub-Actions_Docs-181717?style=for-the-badge&logo=github&logoColor=white)](https://docs.github.com/pt/actions)

</div>

---

<div align="center">

<br/>

**Adriano Carvalho dos Santos** · RA **10747203**  
DevOps & DataOps · Profª **Debora Batista Paulo**

<br/>

![Made with](https://img.shields.io/badge/Made_with-GitHub_Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Deploy](https://img.shields.io/badge/Deploy-GitHub_Pages-222?style=flat-square&logo=githubpages&logoColor=white)
![HTML](https://img.shields.io/badge/Página-site%2Findex.html-E34F26?style=flat-square&logo=html5&logoColor=white)

</div>
