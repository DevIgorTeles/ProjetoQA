# Testes Exploratórios Baseados em Sessão (SBTM) — MedAgenda

## Objetivo
Documentar as sessões de teste exploratório com foco em heurísticas, cenários complexos, suposição de erro e investigação de comportamentos não mapeados nos testes procedurais.

## Metodologia Adotada
- **Session-Based Test Management (SBTM):** Sessões com duração fixa (timebox de 45 minutos), guiadas por um objetivo explícito (*Charter*), com registro de anotações, heurísticas empregadas e defeitos encontrados.

## Sessões Obrigatórias Planejadas (Seção 4.2 do Enunciado)
1. **Sessão 01 — Assistente Virtual (RN18):**
   - *Charter:* Explorar a capacidade do assistente local de orientar procedimentos administrativos sem realizar diagnósticos nem prescrições, testando especialmente gatilhos de urgência médica (SAMU 192) sob variações ortográficas, acentuação, caixa alta/baixa e gírias.
2. **Sessão 02 — Relatórios e Emissão de PDFs (RF09, RF15, RN14, RN16, RN17):**
   - *Charter:* Explorar a geração de relatórios de consultas e financeiro com diferentes períodos (incluindo divisores zero, períodos sem consultas e extremos de 1 ano), comparando minuciosamente a precisão matemática e os dados impressos nos PDFs contra os totais exibidos em tela.

## Modelo de Caderno de Sessão
Cada sessão gera um documento estruturado contendo:
- Identificador da Sessão e Data/Hora;
- Integrante responsável;
- Charter (Missão);
- Estratégia e Áreas Exploradas;
- Anotações e Comportamentos Inesperados;
- Defeitos identificados (referência a `DEF-nnn`).

## Estado Atual
- **Fase 1 (19/11):** Definição dos charters e metodologia no Plano de Testes.
- **Fase 2 (01/12):** Execução das 2 sessões e entrega dos relatórios detalhados.

