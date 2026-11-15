# MedAgenda Validação de Software

Projeto de Teste de Software 2026.2 — Unifacisa. Primeira entrega: ideia, documentação inicial e plano de testes.

## Equipe
Igor Teles; João Pablo; Caio Moura; Jefersson. Matrículas pendentes de informação.

## Objetivo
Planejar a validação do MedAgenda antes de seu uso em clínica, priorizando privacidade, segurança do paciente, integridade do agendamento e consistência dos documentos.

## Estrutura
- `api/` e `web/`: aplicação original fornecida, sem alterações.
- `docs/MedAgenda_Fase_1_Plano_de_Testes.docx`: plano preenchido no modelo oficial.
- `docs/diagramas/`: arquitetura, fluxo de consultas e modelo de dados.
- `tests/{api,e2e,bdd,carga,a11y}/`: espaços das suítes futuras.
- `evidencias/`: resultados futuros, sem dados reais ou credenciais.

## Executar a aplicação
Requisitos: Docker e Docker Compose, 8 GB de RAM e 10 GB de espaço.

```sh
docker compose up --build -d
docker compose ps
```

Interface: http://localhost:8080. API e saúde: http://localhost:3000/api/saude. Banco: mongodb://localhost:27017/medagenda.

Antes de cada lote isolado, restaurar somente o banco de testes:

```sh
docker compose exec api npm run seed
```

Para acompanhar e parar:

```sh
docker compose logs -f api
docker compose down
```

## Contas fictícias do pacote
Admin: admin@medagenda.dev / Admin@2026. Recepção: joana.lima@medagenda.dev / Secretaria@2026. Médica: helena.costa@medagenda.dev / Medico@2026. Paciente: ana.souza@email.dev / Paciente@2026. Exclusivamente demonstração local.

## Planejamento
19/11/2026: plano. 01/12/2026: casos, BDD, explorações e rastreabilidade. 15/12/2026: automação, execução e parecer. O prazo da tarefa no Canvas prevalece.

Ferramentas previstas: Jest, Playwright, Cucumber.js, pdf-parse, k6, axe-core e GitHub Actions. As suítes e o pipeline ainda não estão implementados nesta primeira fase. O plano não declara testes aprovados nem liberação para uso real.

## Origem
Aplicação e especificação fornecidas pelo professor Bruno Rafael Araújo Vasconcelos na disciplina. Este repositório mantém o código recebido e acrescenta os artefatos do grupo; não representa autoria original da aplicação.

## Repositório
https://github.com/DevIgorTeles/ProjetoQA
