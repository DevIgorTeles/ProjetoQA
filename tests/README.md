# Estrutura e Arquitetura de Testes — MedAgenda

Este diretório centraliza todos os artefatos de qualidade, planejamento, especificação, automação e relatórios desenvolvidos pela equipe de QA para a validação do sistema MedAgenda, em cumprimento aos requisitos da disciplina **Teste de Software (2026.2)** da **UNIFACISA**.

Em conformidade com as diretrizes do professor e a norma **ISO/IEC/IEEE 29119-3**, todos os artefatos de teste são mantidos rigorosamente separados da aplicação original (`api/` e `web/`).

---

## 1. Organização dos Diretórios

```text
tests/
├── api/             # Testes automatizados de API REST e matriz de permissões (Jest + Supertest)
├── e2e/             # Testes de ponta a ponta na interface web com Page Objects (Playwright)
├── bdd/             # Especificação executável em BDD / Gherkin (Cucumber.js)
├── carga/           # Testes de desempenho e limites de tempo de resposta (k6)
├── a11y/            # Testes de acessibilidade automatizada WCAG 2.1 AA (axe-core)
├── exploratorios/   # Charters, cadernos de sessão e achados de testes exploratórios
├── casos-de-teste/  # Especificação formal dos casos de teste (modelo CT-nnn) e matriz de rastreabilidade
├── evidencias/      # Registros sanitizados de execução (logs, capturas e payloads)
├── relatorios/      # Relatórios consolidados de execução e cobertura
└── README.md        # Guia geral da arquitetura de testes (este arquivo)
```

---

## 2. Visão Geral por Categoria de Teste

| Diretório | Foco / Escopo | Ferramenta Principal | Entrega Prevista |
| :--- | :--- | :--- | :---: |
| **`api/`** | Regras de negócio (RN01 a RN19), códigos HTTP (RNF01) e permissões por perfil (3.1) | Jest + Supertest / Axios | Entrega 3 (15/12) |
| **`e2e/`** | 5 fluxos principais de usuário navegando com Page Objects nos navegadores Chrome e Firefox | Playwright | Entrega 3 (15/12) |
| **`bdd/`** | Cenários Gherkin (Dado/Quando/Então) cobrindo regras críticas com Esquema do Cenário | Cucumber.js | Entrega 2 (01/12) e Entrega 3 (15/12) |
| **`carga/`** | Desempenho e thresholds da RNF03 (50 VUs, p95 < 800 ms, erros < 1%) | k6 | Entrega 3 (15/12) |
| **`a11y/`** | Acessibilidade nas 4 telas chave da RNF04 (Login, Agendamento, Notificações, Assistente) | axe-core + Playwright | Entrega 3 (15/12) |
| **`exploratorios/`** | Sessões baseadas em charters focadas no Assistente Virtual e Relatórios/PDFs | Sessões SBTM (45 min) | Entrega 2 (01/12) |
| **`casos-de-teste/`** | Mínimo de 50 casos formais (PE, AVL, TD, TE, SE) e Matriz RF/RN/RNF → CT | Modelo oficial CT-nnn | Entrega 2 (01/12) |
| **`evidencias/`** | Evidências sanitizadas de execução (sem dados reais ou tokens persistentes) | Capturas, JSONs, PDFs | Entrega 3 (15/12) |
| **`relatorios/`** | Saídas consolidadas de testes, cobertura e relatórios de execução no CI | HTML / Markdown | Entrega 3 (15/12) |

---

## 3. Estado Atual dos Artefatos (Primeira Entrega — 19/11)

Na **Primeira Entrega (Marco 19/11)**, o foco é a formalização do **Plano de Testes** (`docs/MedAgenda_Fase_1_Plano_de_Testes.docx`), da documentação técnica e da infraestrutura de qualidade.

As suítes automatizadas de código e a execução física dos testes serão desenvolvidas nos marcos seguintes:
- **Entrega 2 (01/12):** Casos de teste formais, BDD inicial e relatórios exploratórios;
- **Entrega 3 (15/12):** Implementação dos testes automatizados, pipeline no GitHub Actions e parecer final.

Nenhum resultado fictício é gerado nesta fase, preservando a transparência e a integridade acadêmica.

