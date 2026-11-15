# Registro de Evidências de Teste — MedAgenda

## Objetivo
Armazenar e organizar as evidências auditáveis das execuções de testes manuais e automatizados, vinculadas diretamente aos casos de teste (`CT-nnn`) e aos relatórios de defeito (`DEF-nnn`).

## Políticas de Segurança e Privacidade (LGPD / RNF02)
- **Sanitização de Dados:** É estritamente proibido o uso de dados de pessoas reais (CPFs reais, nomes reais, telefones reais). Toda a massa é baseada nos dados sintéticos do `seed` oficial.
- **Sanitização de Credenciais:** As capturas de tela e logs de API devem ofuscar ou omitir tokens JWT, senhas e chaves de ambiente.
- **Formato das Evidências:**
  - *Capturas de tela:* Arquivos `.png` ou `.webp` identificados por `CT-nnn_descricao.png` ou `DEF-nnn_evidencia.png`;
  - *Logs de API:* Payloads de requisição e resposta formatados em JSON;
  - *Documentos:* Arquivos `.pdf` baixados durante a verificação de receitas, atestados e comprovantes.

## Estado Atual
- **Fase 1 (19/11):** Definição da estrutura e diretrizes de integridade.
- **Fase 3 (15/12):** Coleta e arquivamento das evidências de execução da suíte completa.

