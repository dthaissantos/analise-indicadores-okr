# Mini diagnóstico de métricas & decisão

**Prevenção a Fraudes | Regra de Velocity**

**Thais Santos — atividade acadêmica com case hipotético.** Contexto: KPIs, OKRs e dupla checagem na disciplina Dados e Analytics nas Organizações, do MBA em Inteligência de Dados & Analytics para Negócios da Universidade Presbiteriana Mackenzie.

## Análise de Regra de Velocity

### Redução de falsos positivos em sistema antifraude

Uma regra de velocity utilizada em um sistema antifraude apresenta volume elevado de alertas que posteriormente não se confirmam como fraude. O diagnóstico propõe avaliar, a partir de dados históricos, se a parametrização atual representa adequadamente os diferentes comportamentos transacionais e se existem oportunidades de reestruturação da regra.

## 1. Introdução & contexto

Regras de velocity são utilizadas em sistemas antifraude para identificar comportamentos transacionais potencialmente suspeitos a partir da frequência, quantidade ou concentração de transações em determinado intervalo de tempo.

No cenário considerado neste diagnóstico, uma regra de velocity apresenta volume elevado de alertas que posteriormente são classificados como falsos positivos, indicando a necessidade de avaliar sua efetividade e sua capacidade de distinguir comportamentos fraudulentos de comportamentos legítimos.

O diagnóstico busca avaliar, com base em dados históricos, se a parametrização atual deve ser mantida, recalibrada ou segmentada, considerando diferentes critérios transacionais e preservando a capacidade de detecção de fraude.

## 2. Problema & decisão

Para este diagnóstico, considera-se uma regra fictícia em que 3 ou mais transações realizadas em menos de 2 minutos no mesmo estabelecimento geram um alerta. O cenário apresenta volume elevado de alertas que posteriormente não se confirmam como fraude.

**Hipótese considerada:** a parametrização atual pode não representar adequadamente diferentes comportamentos transacionais, fazendo com que operações legítimas e potencialmente fraudulentas sejam avaliadas pelo mesmo critério.

**Decisão:** avaliar se a regra atual de velocity deve ser mantida, recalibrada ou segmentada em critérios distintos, buscando reduzir falsos positivos sem comprometer a capacidade de detecção de fraude.

## 3. Pesquisa & evidências

A análise propõe utilizar dados históricos de transações e fraudes confirmadas para avaliar se a regra atual de velocity representa adequadamente diferentes comportamentos transacionais. Como não há base disponível nesta atividade, os critérios abaixo são tratados como hipóteses a serem validadas.

### Campos necessários para a análise

| Campo | Finalidade na análise |
| --- | --- |
| id_transacao | Identificar cada transação e evitar duplicidades. |
| data_hora_transacao | Calcular intervalos e reconstruir a sequência transacional. |
| id_cartao / token | Identificar recorrência do mesmo cartão sem expor dado sensível. |
| id_estabelecimento | Avaliar concentração de transações no mesmo estabelecimento. |
| valor_transacao | Avaliar repetição, valores baixos, arredondados e concentração de valor. |
| status_transacao | Comparar transações aprovadas e recusadas no perfil analisado. |
| flag_fraude | Identificar transações posteriormente classificadas como fraude. |

### Hipóteses e análises propostas

| Hipótese | Dados necessários | Onde buscar | Análise proposta | Resultado |
| --- | --- | --- | --- | --- |
| H1 – Critério por cartão | id_estabelecimento, id_cartao, id_transacao, valor_transacao, data_hora_transacao, flag_fraude, status_transacao | Base transacional + base de fraude/chargeback | Verificar recorrência do mesmo cartão em curtos intervalos e comparar frequência, valores e status entre casos fraudulentos e legítimos. | A validar |
| H2 – Critério por estabelecimento | id_estabelecimento, id_cartao, data_hora_transacao, valor_transacao, id_transacao, flag_fraude, status_transacao | Base transacional + base de fraude/chargeback | Verificar múltiplos cartões em sequência no mesmo estabelecimento e comparar frequência, intervalo, valor e status entre casos fraudulentos e legítimos. | A validar |
| H3 – Critério temporal | data_hora_transacao, flag_fraude, id_estabelecimento, valor_transacao, id_transacao, status_transacao | Base transacional + base de fraude/chargeback | Avaliar a variação da janela de tempo da regra (ex: 2 min, 5 min, 10 min), vinculando obrigatoriamente a análise a dados transacionais maturados (janela de 60 a 90 dias). Isso evita classificar fraudes ainda não notificadas via chargeback como falsos positivos precoces. | A validar |
| H4 – Parametrização genérica | Campos utilizados em H1, H2 e H3 + registro da regra acionada | Base transacional + histórico de alertas/regras | Comparar os padrões encontrados e simular o comportamento da regra atual de 3 transações em 2 minutos sobre diferentes perfis. | A validar a partir de H1, H2 e H3 |

## 4. Métricas & objetivos

| Tipo | Indicador | Cálculo / Função | Por que importa |
| --- | --- | --- | --- |
| KPI 1 | Taxa de falsos positivos | Alertas classificados como legítimos ÷ total de alertas da regra | Mede diretamente o problema que motivou o diagnóstico. |
| KPI 2 | Taxa de detecção de fraude associada a velocity | Fraudes capturadas pela regra ÷ fraudes elegíveis com padrão compatível com velocity | Evita reduzir falsos positivos sacrificando capacidade de detecção. |
| Leading | Taxa de acionamento da regra | Acompanhar variação no volume de alertas após mudanças de parametrização | Mostra rapidamente alteração de sensibilidade. |
| Lagging | Taxa de falsos positivos confirmados | Taxa de Chargeback Maturado (M+2 / 60 a 90 dias). Por que importa: Avalia a precisão real da regra apenas após a maturação total das disputas de fraude, garantindo que o indicador do desfecho seja confiável. | Mostra a precisão efetiva após o resultado. |

*O universo de fraudes elegíveis deverá ser definido após a identificação dos padrões transacionais associados a velocity.*

## 5. OKR

**Objetivo:** aumentar a efetividade da regra de velocity, reduzindo falsos positivos sem comprometer a detecção de fraude.

| Key Result | Meta |
| --- | --- |
| KR1 | Reduzir a taxa de falsos positivos em relação ao baseline atual. |
| KR2 | Manter ou elevar a taxa de detecção das fraudes associadas a padrões de velocity. |
| KR3 | Reduzir acionamentos sobre comportamentos legítimos após eventual reestruturação. |

**Risco:** reduzir falsos positivos apenas tornando a regra mais permissiva pode aumentar a passagem de fraudes. Por outro lado, maximizar a detecção pode ampliar o impacto sobre transações legítimas.

**Proteção:** avaliar conjuntamente falsos positivos e detecção de fraude. Caso os dados sustentem a hipótese de comportamentos distintos, poderão ser simuladas regras segmentadas por cartão, estabelecimento, valor e janela temporal.

**Critérios candidatos para simulação:**

- Mesmo cartão realizando múltiplas transações em curto intervalo.
- Mesmo cartão acumulando valor aprovado igual ou superior a um limite em determinada janela.
- Mesmo estabelecimento processando vários cartões distintos em curto intervalo.

## 6. Dupla checagem

A dupla checagem seguiu a lógica: primeira análise → confronto das hipóteses → verificação das fontes → interpretação final. A segunda checagem revisou as hipóteses, métricas e proposta de reestruturação da regra de velocity, buscando identificar afirmações excessivas, lacunas de evidência e possíveis interpretações alternativas.

| Tema | Posição da primeira análise | Segunda checagem | Posição após verificação |
| --- | --- | --- | --- |
| Parametrização genérica | Pode contribuir para falsos positivos | Manter como hipótese principal. A parametrização genérica pode contribuir para os falsos positivos, mas essa relação precisa ser validada com dados históricos. | Mantido. |
| Segmentação da regra | Hipótese a testar | Manter como hipótese prioritária. Avançar para simulação histórica antes de qualquer alteração em produção. | Mantido. |
| Critério por cartão | Possível padrão de velocity | Manter como hipótese de análise e incluir no plano de simulação histórica. | Mantido. |
| Critério por estabelecimento | Possível padrão de velocity | Manter como hipótese de análise e incluir no plano de simulação histórica. | Mantido. |
| Janela temporal | Threshold atual pode não representar todos os padrões | Reformular. (Ajustar threshold e vincular obrigatoriamente à janela de maturação de dados de 60/90 dias). | Questionei e adaptei referente ao apontamento da segunda checagem, faz sentido aumentar a janela temporal, devido prazos de fraudes os quais levam de 30 a 60 dias para serem confirmadas (levando em consideração o chargeback). |

## 7. Conclusão & recomendação

Com base no diagnóstico conceitual e na dupla checagem das hipóteses, a recomendação é manter a regra genérica atual como referência de controle e avaliar, a partir do histórico transacional e de fraudes confirmadas, se critérios adicionais de velocity por cartão, estabelecimento e valor melhoram a capacidade de discriminar comportamentos fraudulentos e legítimos.

A evolução proposta não substitui imediatamente a regra atual. O objetivo é comparar a performance da parametrização genérica com regras segmentadas e, somente após essa comparação, decidir se algum critério deve ser incorporado ao grupo de velocity.

| Posição | Síntese |
| --- | --- |
| Manter regra genérica | Preservar a regra atual de 3 transações em 2 minutos como baseline para comparação. |
| Avaliar velocity por cartão | Testar se recorrência, valor acumulado e status de transações do mesmo cartão aumentam a capacidade de identificar padrões fraudulentos. |
| Avaliar velocity por estabelecimento | Testar se múltiplos cartões utilizados em sequência no mesmo estabelecimento apresentam comportamento distinto entre fraude e legítimo. |
| Avaliar velocity por valor | Testar se repetição, acumulação ou concentração de valores em determinada janela temporal agrega poder de detecção. |
| Recalibrar janela temporal | Comparar diferentes combinações de quantidade de transações e intervalo de tempo com base no histórico observado. |
| Governança / Goodhart | Incorporar novos critérios apenas se houver redução de falsos positivos sem deterioração relevante da taxa de detecção de fraude. |

## Referências de estrutura

Wikipedia. ISO 8583. Enciclopédia colaborativa online. Disponível em: https://en.wikipedia.org/wiki/ISO_8583. Acesso em: 31 ago. 2026.

**Nota metodológica:** não foi disponibilizada base transacional para esta atividade. As hipóteses, critérios de análise e possíveis reestruturações da regra foram construídos a partir do cenário fictício proposto, dos materiais da disciplina, de referências conceituais e de conhecimento de domínio adquirido no contexto profissional. Nenhuma hipótese foi tratada como conclusão comprovada sem validação por dados históricos.
