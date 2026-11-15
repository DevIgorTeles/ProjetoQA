# Especificação de Casos de Teste e Rastreabilidade — MedAgenda

## Objetivo
Centralizar a especificação formal de todos os casos de teste planejados para a validação do sistema MedAgenda, em estrito alinhamento ao modelo da seção 7.1 do edital e à norma **ISO/IEC/IEEE 29119-3**.

## Metas de Cobertura (Entrega 2 — 01/12)
- **Quantidade mínima:** 50 casos de teste especificados;
- **Cobertura total:** 100% dos requisitos funcionais (RF01 a RF15), regras de negócio (RN01 a RN19), requisitos não funcionais (RNF01 a RNF07) e linhas da matriz de permissões (seção 3.1).
- **Técnicas Formais de Caixa-Preta Obrigatórias:**
  1. *Partição de Equivalência (PE):* Classes válidas e inválidas de dados cadastrais, e-mail, senha e CPF;
  2. *Análise de Valor Limite (AVL):* Testes de fronteira em nomes (2, 3, 120, 121 caracteres), antecedência de agendamento (119, 120, 121 min), limite de consultas (2, 3, 4 ativas), cancelamento (23h59, 24h, 24h01) e atestado médico (-1, 0, 15, 16 dias);
  3. *Tabela de Decisão (TD):* Combinações de permissão por perfil (ADMIN, SECRETARIA, MEDICO, PACIENTE) e elegibilidade de retorno gratuito (RN10);
  4. *Transição de Estados (TE):* Ciclo de vida da consulta médica (RN11) e bloqueio de transições a partir de estados finais;
  5. *Suposição de Erro (SE):* Ações repetidas (duplo clique), recarga de página e requisições com IDs malformados.

## Estrutura do Caso de Teste (Modelo Oficial Seção 7.1)
| Campo | Descrição |
| :--- | :--- |
| **ID** | Identificador único no formato `CT-nnn` |
| **Requisito** | RF, RN, RNF ou item da matriz de permissões associado |
| **Título** | Descrição clara e concisa do objetivo do teste |
| **Técnica** | Técnica formal aplicada (PE, AVL, TD, TE, SE) |
| **Pré-condições** | Estado do banco, usuário logado e massa necessária |
| **Passos / Entrada** | Sequência ordenada de ações e dados de entrada |
| **Resultado Esperado** | Comportamento especificado (mensagens, códigos HTTP, alterações no banco) |
| **Resultado Obtido** | *Preenchido exclusivamente na execução (Fase 3)* |
| **Situação** | *Passou / Falhou / Bloqueado (Fase 3)* |
| **Evidência** | *Link para evidência arquivada (Fase 3)* |

## Matriz de Rastreabilidade
Será mantida a matriz bidirecional cruzando:
`Requisito (RF/RN/RNF) <---> Caso de Teste (CT-nnn) <---> Script de Automação <---> Defeito (DEF-nnn)`

## Estado Atual
- **Fase 1 (19/11):** Definição das técnicas e padrões.
- **Fase 2 (01/12):** Publicação dos ≥50 casos de teste e da Matriz de Rastreabilidade.

