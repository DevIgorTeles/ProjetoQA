# Testes de Carga e Desempenho — MedAgenda

## Objetivo
Avaliar o comportamento, a estabilidade e os tempos de resposta da API do MedAgenda sob concorrência, verificando o cumprimento estrito do requisito não funcional **RNF03**.

## Critérios e Limites Oficiais (RNF03)
- **Concorrência:** 50 usuários simultâneos (VUs — Virtual Users);
- **Percentil 95 (p95):** Menor que 800 ms nos endpoints críticos;
- **Taxa de Erro:** Menor que 1% de falhas HTTP (respostas 5xx ou timeouts);
- **Endpoints Chave:**
  - `GET /api/medicos/:id/horarios?data=AAAA-MM-DD` (consulta de horários livres);
  - `GET /api/consultas?data=AAAA-MM-DD` (listagem da agenda do dia).

## Ferramental Previsto
- **Ferramenta:** k6 (Grafana Labs)
- **Métricas avaliadas:** `http_req_duration{p(95)}`, `http_req_failed`, taxa de requisições por segundo (RPS)
- **Estratégia:** Ramp-up de 1 minuto (aquecimento) seguido de patamar sustentado de 5 minutos com 50 VUs.

## Estado Atual
- **Fase 1 (19/11):** Definição dos thresholds no plano de testes.
- **Fase 3 (15/12):** Script k6 executável e relatórios de métricas.

