# MedAgenda — Plano de Testes e Validação de Software

Projeto acadêmico desenvolvido para a disciplina **223704 - ELABORAR PLANO DE TESTES E VALIDAÇÃO DE UM SOFTWARE - NOITE (2026.2)** do curso de **Ciências da Computação** do **Centro Universitário UNIFACISA**, ministrada pelo **Prof. Bruno Rafael Araújo Vasconcelos**.

O projeto consiste na elaboração do **Plano de Testes e Validação** e na condução das atividades de garantia da qualidade (QA) para o sistema médico-hospitalar **MedAgenda**, fundamentando-se nos padrões da norma internacional **ISO/IEC/IEEE 29119-3 (Test Documentation)**.

---

## 1. Equipe de Qualidade e Responsabilidades

| Integrante | Matrícula | Responsabilidade Principal no Projeto | Revisor Par |
| :--- | :---: | :--- | :--- |
| **Igor Teles de Farias** | `2313081170` | Coordenação geral, gestão de requisitos, autenticação, controle de permissões (Seção 3.1), testes de API e matriz de rastreabilidade | João Pablo Delgado Gomes |
| **João Pablo Delgado Gomes** | `2313081109` | Regras temporais e agendamento (RN07–RN12), especificação de casos de teste e suíte E2E com Page Objects | Caio Moura Portela Sousa |
| **Caio Moura Portela Sousa** | `2313080152` | Prontuários médicos, ciclo de atendimento (RN11, RN13), integridade de PDFs (RN14), notificações e cenários BDD | Jefferson Ezequiel Costa Ananias |
| **Jefferson Ezequiel Costa Ananias** | `2313080077` | Relatórios gerenciais e financeiro (RN16, RN17), assistente virtual (RN18), testes de desempenho (k6), acessibilidade (axe) e pipeline CI | Igor Teles de Farias |

---

## 2. O Sistema MedAgenda

O **MedAgenda** é uma aplicação web completa desenvolvida para gerenciar o fluxo operacional de uma clínica médica multiprofissional. O sistema contempla quatro perfis de acesso:
- **Administrador:** Gestão de usuários, criação e ativação/desativação de contas, redefinição de senhas, acompanhamento de indicadores clínicos e relatórios de faturamento.
- **Secretária (Recepção):** Cadastro de fichas de pacientes, agendamento de consultas (horários livres ou encaixes), confirmação de presença, registro de faltas e cancelamentos.
- **Médico:** Acompanhamento da agenda do dia, condução do atendimento em tempo real, registro estruturado de prontuário eletrônico (queixa, anamnese, diagnóstico, conduta, prescrição e atestado) e emissão de documentos clínicos.
- **Paciente:** Autoatendimento via portal para agendamento de consultas com antecedência mínima de 2 horas, cancelamento até 24 horas antes, download de PDFs (comprovante, receita e atestado), central de notificações e interação com assistente virtual para dúvidas administrativas.

### Tecnologias da Aplicação
- **Frontend:** React 18, Vite, React Router, servido via Nginx.
- **Backend API:** Node.js 20, Express, Mongoose, autenticação JWT (expiração de 8h), geração de documentos PDF com PDFKit.
- **Banco de Dados:** MongoDB 7.
- **Infraestrutura:** Docker Compose gerenciando 3 contêineres interdependentes com verificação de saúde (*healthcheck*).

---

## 3. Estrutura do Repositório

O repositório está organizado de modo a preservar integralmente a aplicação fornecida pelo professor na raiz, mantendo todos os artefatos de qualidade e testes estritamente desacoplados:

```text
.
├── docker-compose.yml          # Definição e orquestração dos serviços (Mongo, API e Web)
├── .gitignore                  # Regras de exclusão para Git (dependências, logs, volumes)
├── README.md                   # Documentação técnica do projeto (este arquivo)
│
├── api/                        # Aplicação Backend original fornecida (Node.js + Express + MongoDB)
│   ├── Dockerfile
│   ├── package.json
│   └── src/                    # Rotas, modelos Mongoose, regras de agendamento e seed
│
├── web/                        # Aplicação Frontend original fornecida (React 18 + Vite)
│   ├── Dockerfile
│   ├── package.json
│   └── src/                    # Páginas por perfil, componentes de interface e serviços de API
│
├── docs/                       # Documentação formal e modelos do projeto
│   ├── MedAgenda_Fase_1_Plano_de_Testes.docx  # Plano de Testes formal da Entrega 1
│   └── diagramas/                             # Diagramas conceituais do sistema
│       ├── arquitetura.png                    # Diagrama de Arquitetura e Comunicação
│       ├── fluxo.png                          # Fluxo e Ciclo de Vida da Consulta Médica
│       └── dados.png                          # Modelo Entidade-Relacionamento Lógico
│
└── tests/                      # Estrutura modular dos artefatos de teste do grupo
    ├── README.md               # Guia geral da arquitetura de testes e ciclo de vida
    ├── api/                    # Planejamento e suíte de testes de API REST e permissões
    ├── e2e/                    # Planejamento e suíte de testes ponta a ponta (Page Objects)
    ├── bdd/                    # Especificações executáveis em Gherkin (Dado/Quando/Então)
    ├── carga/                  # Testes de desempenho e conformidade de thresholds k6
    ├── a11y/                   # Testes de acessibilidade digital WCAG 2.1 AA (axe-core)
    ├── exploratorios/          # Cadernos de sessão e charters (Assistente e Relatórios)
    ├── casos-de-teste/         # Especificação formal dos casos de teste (modelo CT-nnn)
    ├── evidencias/             # Repositório de evidências sanitizadas de execução
    └── relatorios/             # Relatórios consolidados de qualidade, cobertura e parecer
```

---

## 4. Instruções de Instalação e Execução

### 4.1 Pré-requisitos
- **Docker Desktop** (Windows/macOS) ou **Docker Engine com plugin Docker Compose** (Linux).
- Pelo menos **8 GB de memória RAM** e **10 GB livres em disco**.
- Portas de rede locais disponíveis: `8080` (Web), `3000` (API REST) e `27017` (MongoDB).

### 4.2 Inicialização do Ambiente
Para construir as imagens e iniciar todos os serviços em segundo plano:

```bash
docker compose up --build -d
```

Verifique se os três contêineres estão saudáveis e operacionais:

```bash
docker compose ps
```

### 4.3 Endereços de Acesso Local
| Serviço | Endereço | Descrição / Retorno Esperado |
| :--- | :--- | :--- |
| **Interface Web** | `http://localhost:8080` | Tela de autenticação do MedAgenda |
| **API REST (Healthcheck)** | `http://localhost:3000/api/saude` | `{"status":"ok","servico":"medagenda-api"}` |
| **Banco de Dados** | `mongodb://localhost:27017/medagenda` | Acesso administrativo via MongoDB Compass ou mongosh |

### 4.4 Restauração da Massa de Dados Inicial (`Seed`)
Na primeira execução, o banco é automaticamente populado com 3 médicos especialistas, 10 fichas de pacientes e cerca de 200 consultas distribuídas entre histórico passado, atendimentos de hoje e semanas futuras.

Para restaurar o banco ao estado inicial padronizado antes ou depois de cada campanha de testes:

```bash
docker compose exec api npm run seed
```

> [!NOTE]
> As datas do seed são calculadas dinamicamente com base na data do sistema no momento da execução. Por isso, os testes de agendamento calculam datas úteis em tempo relativo, e não através de datas fixas no passado.

### 4.5 Encerramento do Ambiente
- Para parar os serviços preservando os dados no volume:
  ```bash
  docker compose down
  ```
- Para parar os serviços e reiniciar o banco do zero na próxima subida:
  ```bash
  docker compose down -v
  ```
- Para acompanhar os logs da API em tempo real:
  ```bash
  docker compose logs -f api
  ```

---

## 5. Contas Fictícias de Demonstração

O ambiente possui as seguintes contas pré-configuradas para validação manual e testes automatizados:

| Perfil | E-mail de Acesso | Senha | Contexto e Especialidade no Sistema |
| :--- | :--- | :--- | :--- |
| **Administrador** | `admin@medagenda.dev` | `Admin@2026` | Acesso irrestrito a usuários, relatórios e auditoria |
| **Médica** | `helena.costa@medagenda.dev` | `Medico@2026` | Clínica Geral · Seg a Sex, 08h–12h e 14h–18h (30 min) |
| **Médico** | `ricardo.alves@medagenda.dev` | `Medico@2026` | Cardiologia · Ter e Qui, 08h–17h (40 min) |
| **Médica** | `marina.duarte@medagenda.dev` | `Medico@2026` | Pediatria · Seg, Qua e Sex, 13h–18h (20 min) |
| **Secretária** | `joana.lima@medagenda.dev` | `Secretaria@2026` | Recepção ativa (cadastro, agendamento, confirmação) |
| **Secretário** | `pedro.santos@medagenda.dev` | `Secretaria@2026` | Conta intencionalmente desativada (ex-funcionário) |
| **Paciente** | `ana.souza@email.dev` | `Paciente@2026` | 3 consultas ativas futuras; alergia a dipirona |
| **Paciente** | `carlos.lima@email.dev` | `Paciente@2026` | Consultas no histórico realizadas para teste de retorno |
| **Paciente** | `fernanda.rocha@email.dev` | `Paciente@2026` | Convênio Saúde Vida; histórico de falta registrada |
| **Paciente** | `luiza.costa@email.dev` | `Paciente@2026` | Atendimento particular; alergia a penicilina |

Existem também 6 pacientes cadastrados sem conta digital associada (atendimento exclusivo via recepção): *Miguel, Roberto, Patrícia, Thiago, Helena Vitória e José*.

---

## 6. Configuração e Estratégia do Ambiente de Testes

A infraestrutura de qualidade foi desenhada respeitando as seguintes premissas metodológicas:

1. **Testes de API e Permissões:**
   - **Ferramental:** Jest com chamadas HTTP diretas via Supertest/Axios.
   - **Escopo:** Validação das regras de negócio (RN01 a RN19), códigos de status HTTP conforme RNF01 (201, 400, 401, 403, 404, 409, 422) e conferência da matriz de permissões da Seção 3.1.
2. **Testes de Interface de Ponta a Ponta (E2E):**
   - **Ferramental:** Playwright Test adotando o padrão arquitetural **Page Object Model (POM)**.
   - **Escopo:** Execução automatizada nos navegadores Chromium e Firefox nos viewports Desktop (1280px) e Mobile (390px), cobrindo os 5 fluxos essenciais:
     1. Paciente: agendamento com antecedência e cancelamento tempestivo;
     2. Recepção: cadastro de paciente, agendamento e confirmação;
     3. Médico: início do atendimento, prontuário estruturado e emissão de receita;
     4. Administrador: gestão de contas de acesso e redefinição de senhas;
     5. Relatórios: extração e download auditado de relatórios gerenciais e financeiros.
3. **Verificação de Documentos PDF:**
   - **Ferramental:** Automação de download combinada com a biblioteca `pdf-parse`.
   - **Escopo:** Validação de cabeçalho, CRM do médico, nome do paciente e integridade textual em comprovantes, receitas e atestados médicos (RN14).
4. **Testes Baseados em BDD:**
   - **Ferramental:** Cucumber.js com especificações em linguagem ubíqua Gherkin (`.feature`).
   - **Escopo:** Formalização de cenários de negócio complexos (cancelamento RN12, blocos de grade RN07 e regras de retorno RN10).
5. **Testes de Desempenho (Carga):**
   - **Ferramental:** k6 (Grafana Labs).
   - **Escopo:** Validação dos limites estipulados no requisito RNF03 (50 usuários simultâneos, p95 < 800 ms e taxa de erro < 1% na listagem de horários e agenda).
6. **Testes de Acessibilidade Digital:**
   - **Ferramental:** `@axe-core/playwright` e auditoria manual via navegação por teclado.
   - **Escopo:** Avaliação dos critérios WCAG 2.1 nível AA (contraste mínimo de 4,5:1, rótulos acessíveis e navegação completa por teclado) nas telas de Login, Agendamento, Notificações e Assistente Virtual (RNF04).

---

## 7. Cronograma e Entregas do Projeto Acadêmico

| Marco | Data Limite | Conteúdo da Entrega | Situação Atual |
| :---: | :---: | :--- | :---: |
| **Entrega 1** | **Qui 19/11/2026** | **Plano de Testes e Validação Formal:** Documento `MedAgenda_Fase_1_Plano_de_Testes.docx` (ISO 29119-3), repositório Git organizado, diagramas conceituais e README técnico | **Artefatos locais finalizados; pendente submissão no Canvas** |
| **Entrega 2** | **Ter 01/12/2026** | **Projeto de Casos de Teste:** Mínimo de 50 casos formais (PE, AVL, TD, TE, SE), cenários Gherkin, relatórios de 2 sessões exploratórias (Assistente e Relatórios) e Matriz de Rastreabilidade | *Previsto para a próxima fase* |
| **Entrega Final** | **Ter 15/12/2026** | **Automação e Parecer Final:** Suíte automatizada executável no CI (GitHub Actions), relatórios de defeito (`DEF-nnn`), parecer de validação, vídeo explicativo e apresentação | *Previsto para a etapa final* |

> [!IMPORTANT]
> **Nota de Transparência Acadêmica:** Nesta primeira entrega (Fase 1), o repositório estabelece a infraestrutura de pastas, a documentação formal e o plano de validação. Nenhuma suíte de teste automatizado é declarada como executada prematuramente, e nenhum resultado fictício de validação é informado.

---

## 8. Conformidade com as Regras de Submissão

- **Repositório GitHub:** [https://github.com/DevIgorTeles/ProjetoQA](https://github.com/DevIgorTeles/ProjetoQA) (público ou com acesso liberado ao professor).
- **Submissão no Canvas Instructure:** Conforme a instrução da UNIFACISA, o envio da tarefa é realizado estritamente por **URL do documento online** (Google Docs / OneDrive), mantendo compartilhamento com o e-mail institucional do docente (`bruno.vasconcelos@maisunifacisa.com.br`) com nível Editor/Comentarista.
