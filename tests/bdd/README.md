# Testes em BDD (Behavior-Driven Development) — MedAgenda

## Objetivo
Especificar e automatizar o comportamento do sistema MedAgenda em linguagem ubíqua e colaborativa utilizando a sintaxe **Gherkin** (`Funcionalidade`, `Contexto`, `Cenário`, `Esquema do Cenário`, `Dado`, `Quando`, `Então`).

## Ferramental Previsto
- **Framework:** Cucumber.js
- **Linguagem:** Gherkin em Português (`# language: pt`)
- **Integração:** Automação dos step definitions via chamadas HTTP (API) ou Playwright

## Regras de Negócio Selecionadas
Conforme especificação da seção 4.2 e 4.4 do enunciado:
1. **RN12 — Cancelamento de consulta pelo paciente com prazo limite de 24 horas:**
   - Cenário com antecedência > 24h (sucesso no cancelamento).
   - Cenário com antecedência < 24h (recusa e orientação para procurar a recepção).
2. **RN07 — Agendamento de consultas dentro dos blocos da agenda e sobreposição:**
   - Esquema do Cenário testando diferentes dias da semana e horários fora do expediente.
3. **RN10 — Regra de Retorno gratuito em até 30 dias:**
   - Tabela de decisão parametrizada cobrindo mesmo médico, consulta prévia realizada e janela de dias (≤30 e >30 dias).

## Estado Atual
- **Fase 1 (19/11):** Definição das regras candidatas e arquitetura dos steps.
- **Fase 2 (01/12):** Entrega dos arquivos `.feature` com cenários e Esquema do Cenário.
- **Fase 3 (15/12):** Execução automatizada com step definitions no Cucumber.js.

