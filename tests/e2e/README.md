# Testes de Ponta a Ponta (E2E) — MedAgenda

## Objetivo
Validar os fluxos completos do sistema MedAgenda a partir da interface gráfica web (`http://localhost:8080`), simulando as ações de usuários reais nos navegadores Chromium e Firefox, em conformidade com o padrão Page Objects.

## Ferramental Previsto
- **Framework:** Playwright Test
- **Padrão Arquitetural:** Page Object Model (POM)
- **Navegadores:** Chromium, Firefox
- **Viewports (RNF05):** Desktop (1280px) e Mobile (390px)

## Os 5 Fluxos Obrigatórios (Seção 4.4 do Enunciado)
1. **Fluxo Paciente:** Login como paciente, agendamento de consulta com mais de 2h de antecedência e posterior cancelamento dentro do prazo de 24h (RN08, RN12).
2. **Fluxo Recepção:** Login como secretária, cadastro/busca de paciente, agendamento de consulta (livre ou encaixe) e confirmação (RF03, RF05, RF07).
3. **Fluxo Médico:** Login como médico, início de atendimento, preenchimento do prontuário (diagnóstico, conduta, prescrição e atestado) e finalização com emissão de receita (RF08, RN13).
4. **Fluxo Administrador:** Login como admin, criação de nova conta de acesso, edição e redefinição de senha (RF02, RN01, RN03).
5. **Fluxo Relatórios:** Login como admin, consulta de relatórios por período e exportação de PDF conferindo download (RF15, RN16, RN17).

## Estado Atual
- **Fase 1 (19/11):** Definição da arquitetura POM e mapeamento dos 5 fluxos.
- **Fase 3 (15/12):** Implementação dos testes executáveis em Playwright.

