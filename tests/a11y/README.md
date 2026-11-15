# Testes de Acessibilidade Digital — MedAgenda

## Objetivo
Verificar a conformidade das interfaces do MedAgenda com as diretrizes da **WCAG 2.1 nível AA**, em estrito atendimento ao requisito **RNF04**.

## Telas no Escopo de Avaliação (RNF04)
1. **Login:** `http://localhost:8080/login`
2. **Agendamento de Consulta:** `http://localhost:8080/nova-consulta`
3. **Notificações:** `http://localhost:8080/notificacoes`
4. **Assistente Virtual:** `http://localhost:8080/assistente`

## Critérios de Aceitação
- **Nomes Acessíveis:** Todo campo de entrada e botão com rótulo (`aria-label`, `<label for>` ou texto visível inequívoco);
- **Contraste Mínimo:** Razão de contraste de pelo menos 4,5:1 para texto normal contra o fundo;
- **Navegabilidade por Teclado:** Utilização completa de todos os formulários e botões exclusivamente via teclado (`Tab`, `Shift+Tab`, `Enter`, `Espaço`), com indicadores visíveis de foco (`focus visible`).

## Ferramental Previsto
- **Automação:** `@axe-core/playwright`
- **Validação Manual:** Inspeção visual de contraste e navegação assistiva apenas por teclado.

## Estado Atual
- **Fase 1 (19/11):** Definição dos critérios no plano de testes.
- **Fase 3 (15/12):** Execução automatizada com axe e checklist de validação manual por teclado.

