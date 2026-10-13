# Lei de Goodhart em meios de pagamento

**Thais Santos — prática acadêmica com case hipotético.**

**Nível:** MBA, intermediário.  
**Foco:** Lei de Goodhart e decisão orientada por indicadores.

## Contexto do caso

Uma empresa de pagamentos definiu como prioridade aumentar a taxa de aprovação de transações no e-commerce. Há três meses, a liderança estabeleceu a meta de elevar a aprovação de 88% para 93%.

| Período | Taxa de aprovação |
| --- | --- |
| Referência inicial | 88% |
| Mês 1 | 89,5% |
| Mês 2 | 91,2% |
| Mês 3 | 93,4% |

A meta foi atingida. No mesmo período, porém, foram observados:

- Aumento no volume de contestações.
- Crescimento das perdas financeiras associadas a fraude.
- Mais reclamações de compras não reconhecidas.
- Maior aprovação de transações anteriormente classificadas como de risco elevado.

O time responsável considera o projeto bem-sucedido porque o KPI oficial atingiu a meta. A diretoria precisa decidir se mantém a estratégia atual ou modifica a forma como o desempenho é medido e gerenciado.

## 1. Problema ou decisão

O problema não é simplesmente o aumento das fraudes, mas verificar se a estratégia utilizada para elevar a aprovação gerou valor real para o negócio ou apenas melhorou isoladamente o KPI de aprovação.

**Decisão:** avaliar a manutenção da estratégia de aprovação e revisar a medição de desempenho, considerando conjuntamente conversão, risco e impacto financeiro.

## 2. Hipóteses

**Hipótese principal:** a flexibilização dos critérios da esteira antifraude para aumentar a taxa de aprovação permitiu maior passagem de transações de alto risco, fazendo com que parte do ganho de aprovação fosse acompanhado por aumento das perdas financeiras.

Hipóteses adicionais a validar:

- Determinados lojistas, MCCs ou perfis transacionais podem concentrar grande parte do aumento de fraude.
- Regras ou thresholds do antifraude podem ter sido alterados para reduzir recusas.
- Transações anteriormente recusadas podem ter passado a ser aprovadas sem melhoria equivalente na capacidade de discriminar fraude de transação legítima.
- O aumento das perdas pode estar relacionado ao crescimento do TPV, e não exclusivamente à alteração da aprovação.
- Pode ter ocorrido mudança externa no comportamento fraudulento, incluindo possível atuação coordenada de uma quadrilha.

## 3. Dados e indicadores necessários

| Dado | Finalidade |
| --- | --- |
| ID do lojista | Identificar concentração por estabelecimento. |
| ID da transação | Identificar cada operação de forma única. |
| Data e hora | Analisar evolução temporal e padrões. |
| Valor da transação | Medir TPV e exposição financeira. |
| Resultado da transação | Identificar aprovação ou recusa. |
| Score ou faixa de risco | Comparar aprovação por nível de risco. |
| Regra ou decisão do antifraude | Identificar o motivo da aprovação ou recusa. |
| Flag de fraude ou reporte | Identificar transações posteriormente reportadas. |
| Flag de chargeback | Identificar transações contestadas. |
| Valor do chargeback ou perda | Quantificar impacto financeiro. |
| MCC | Analisar comportamento por segmento. |
| Cartão mascarado ou token | Investigar recorrência sem expor dados sensíveis. |
| Motivo do chargeback | Separar fraude de outros tipos de contestação. |

### Etapa 1 — Comparação temporal

Compararia os períodos antes e depois do aumento da aprovação, utilizando:

- Taxa de aprovação.
- TPV aprovado.
- Quantidade e valor de chargebacks.
- Taxa de chargeback.
- Quantidade e valor de fraudes confirmadas.
- Taxa de fraude.
- Perda financeira sobre TPV.
- Reclamações por compras não reconhecidas.

### Etapa 2 — Análise por faixa de risco

Analisaria o comportamento das transações e validaria o risco por faixa, comparando:

- Quantidade de tentativas.
- Quantidade aprovada.
- Taxa de aprovação.
- TPV aprovado.
- Fraude confirmada.
- Chargeback.
- Perda financeira.

### Etapa 3 — Identificação de padrões e concentrações

Investigaria a concentração por:

- Lojista.
- MCC.
- Faixa de valor.
- Horário.
- Cartão ou token.
- Regra antifraude.
- Faixa de risco.

### Etapa 4 — Avaliação do impacto econômico

Calcularia a receita líquida ajustada:

**Receita líquida ajustada = Receita de MDR − Perdas por fraude − Custos operacionais de chargeback.**

Se o saldo for negativo, as receitas consideradas não cobrem as perdas e os custos associados às transações aprovadas.

## 4. Riscos e limitações

### Volume

O crescimento absoluto de fraude ou chargeback não demonstra sozinho piora. Se houve crescimento expressivo do TPV, é necessário analisar taxas relativas, além de quantidades e valores absolutos.

### Defasagem temporal

Chargebacks podem aparecer depois da transação. As transações do mês 3 podem ainda não ter maturado completamente; comparar períodos sem considerar essa defasagem pode subestimar o risco mais recente.

### Mudanças simultâneas

Outros fatores podem ter ocorrido nos três meses:

- Crescimento do volume.
- Entrada de novos lojistas.
- Mudança no perfil de clientes.
- Sazonalidade.
- Ataque fraudulento externo.
- Alteração de regras antifraude.

**Correlação temporal não significa necessariamente causalidade.**

### Qualidade dos dados

Validaria:

- Duplicidade de transações.
- Preenchimento das flags.
- Consistência da classificação de fraude.
- Definição uniforme de chargeback.
- Versão das regras antifraude.
- Ausência de alterações retroativas nos registros.

## 5. KPI, KRI e indicadores leading/lagging

| Classificação | Indicador | Papel na decisão |
| --- | --- | --- |
| KPI principal | Taxa de aprovação | Acompanhar o objetivo de conversão. |
| KPI secundário / KRI | Perdas por fraude sobre o TPV | Acompanhar a exposição financeira em relação ao volume. |
| Leading | Percentual de transações de alto risco | Sinalizar a exposição ao risco antes da confirmação das perdas. |
| Lagging | Taxa de chargeback e perda confirmada | Avaliar os desfechos após a maturação dos dados. |

O TPV pode ter aumentado ao mesmo tempo que os chargebacks e as perdas. A avaliação deve considerar a evolução conjunta desses indicadores.

## 6. Teste de Goodhart

| Elemento | Aplicação ao caso |
| --- | --- |
| Resultado real desejado | Aprovar o maior número possível de transações legítimas, mantendo risco e perdas em níveis aceitáveis. |
| Métrica utilizada | Taxa de aprovação. |
| Otimização realizada | Aumentar a aprovação de 88% para 93%. |
| Possível distorção | Aprovar mais transações arriscadas para atingir a meta. |

O caso apresenta um possível efeito da Lei de Goodhart: a melhoria da métrica pode deixar de representar o resultado real desejado quando a aprovação é otimizada isoladamente. Essa distorção permanece uma hipótese a validar.

## 7. Conclusão e recomendação

Recomendo realizar uma validação dos indicadores por meio de uma análise temporal e segmentada, identificando quais lojistas, perfis de transação ou faixas de risco mais contribuíram para o aumento das aprovações e das perdas por fraude.

Até que essa análise seja concluída, a taxa de aprovação não deve ser utilizada isoladamente como medida de sucesso, pois seu crescimento pode estar associado a um aumento da exposição ao risco.

**A recomendação imediata é modificar a forma de medir e gerenciar o desempenho, avaliando conjuntamente aprovação, fraude, chargeback e impacto financeiro.** A decisão sobre manter ou ajustar a estratégia de aprovação deve se apoiar nessa validação, buscando equilíbrio entre conversão e risco.

---

**Nota metodológica:** esta análise parte de um cenário acadêmico hipotético. Não foi disponibilizada base transacional; as hipóteses e análises propostas não representam resultados comprovados. Os percentuais de aprovação pertencem ao enunciado do exercício.

[Voltar ao índice do repositório](../../README.md)
