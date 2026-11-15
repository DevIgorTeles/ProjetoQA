# Testes de API — MedAgenda

## Objetivo
Validar as regras de negócio (RN01 a RN19), códigos de status HTTP (RNF01) e a matriz de permissões por perfil (Seção 3.1) diretamente através da API REST do MedAgenda (`http://localhost:3000/api`).

## Ferramental Previsto
- **Framework:** Jest
- **Cliente HTTP:** Supertest / Axios
- **Asserções:** Expect / Chai

## Escopo dos Testes Planejados
1. **Autenticação e Sessão (RF01, RN02, RN03, RN04, RNF02):** Login com perfis válidos, rejeição de credenciais inválidas, contas inativas e expiração de token JWT (8 horas).
2. **Matriz de Permissões (Seção 3.1):** Chamadas diretas de cada perfil (ADMIN, SECRETARIA, MEDICO, PACIENTE) para todos os endpoints, garantindo 403 Forbidden em acessos não autorizados.
3. **Agendamento e Regras Temporais (RN07, RN08, RN09, RN10):** Validação de sobreposição de horários (409 Conflict), limite de 3 consultas futuras (422), antecedência de 2 horas para pacientes e regras de retorno gratuito em 30 dias.
4. **Ciclo de Vida da Consulta (RN11, RN12, RN13):** Transições válidas e bloqueio de alterações em estados finais (REALIZADA, CANCELADA, FALTOU).
5. **Geração e Integridade de PDFs (RF09, RN14):** Validação de cabeçalhos, download e conteúdo via `pdf-parse`.

## Estado Atual
- **Fase 1 (19/11):** Planejamento da suíte e mapeamento de rotas.
- **Fase 3 (15/12):** Implementação dos scripts executáveis e integração ao CI.

