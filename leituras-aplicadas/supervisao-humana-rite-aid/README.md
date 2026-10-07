# Supervisão humana em IA: do alerta à decisão

**Thais Santos | Leitura aplicada | Estudo teórico e documental em desenvolvimento**

## Pergunta que orienta a leitura

A pessoa que recebe um alerta automatizado pode e consegue discordar dele antes que produza uma consequência?

Estudo essa pergunta conectando governança de IA, comportamento humano e responsabilidade organizacional. Meu interesse é compreender as condições que tornam a supervisão humana efetiva e como elas podem ser avaliadas por indicadores.

## O que as fontes apresentam

### Ponto de partida: interações e efeitos coletivos

No ensaio *From the Physics of Society to a Sociology of Artificial Agents*, Mustafa Sahin Bulbul propõe investigar padrões coletivos que surgem das interações entre agentes artificiais. O texto alerta para os limites de atribuir características humanas à IA.

Essa leitura motivou uma pergunta aplicada a outro objeto: como as interações entre tecnologia, pessoas e regras institucionais influenciam decisões? A conexão é uma interpretação minha. Sistemas humano–IA–instituições não são o mesmo objeto das relações IA–IA discutidas no ensaio.

Fonte: [ensaio no arXiv, versão 1, submetida em 13 de setembro de 2026](https://arxiv.org/abs/2609.14751). O registro consultado identifica um ensaio; não utilizo seu argumento como prova de eficácia de uma solução de governança.

### Caso documental: Rite Aid

Em comunicado de dezembro de 2023, a FTC relatou alegações de que o reconhecimento facial utilizado pela Rite Aid entre 2012 e 2020 gerou milhares de correspondências falsamente positivas e de que funcionários agiram contra consumidores com base nesses alertas. A FTC também apontou falhas de avaliação, monitoramento e treinamento.

Esse registro permite examinar o caminho entre alerta técnico e ação organizacional. Não permite concluir que todos os funcionários apresentavam viés de automação ou atribuir a eles um estado psicológico comprovado.

Fontes: [comunicado da FTC](https://www.ftc.gov/news-events/news/press-releases/2023/12/rite-aid-banned-using-ai-facial-recognition-after-ftc-says-retailer-deployed-technology-without) e [petição da FTC](https://www.ftc.gov/system/files/ftc_gov/pdf/2023190_riteaid_complaint_filed.pdf).

## Minha interpretação

A presença de uma pessoa no fluxo não demonstra, por si só, supervisão efetiva. Para questionar um alerta, ela precisa de informação, tempo, treinamento, autoridade e um caminho para registrar ou encaminhar a discordância.

Na minha leitura, o problema precisa ser analisado no conjunto: qualidade da entrada, saída do sistema, interpretação humana, política de ação, monitoramento e possibilidade de contestação. Viés de automação é uma lente para formular perguntas, não uma conclusão comprovada sobre cada pessoa envolvida.

## Aplicação proposta à análise de negócios

A decisão a apoiar seria: quais condições devem existir para que um alerta possa orientar uma ação, e quando o caso precisa de investigação adicional?

| Etapa | Pergunta de análise | Controle proposto |
| --- | --- | --- |
| Entrada | A informação tem origem e qualidade adequadas? | Verificação de qualidade e rastreabilidade. |
| Alerta | O resultado sustenta a interpretação apresentada? | Exposição de evidências e limitações. |
| Revisão | A pessoa consegue discordar e escalar o caso? | Treinamento, tempo e autoridade definidos. |
| Ação | Há justificativa suficiente para a intervenção? | Registro da decisão e do responsável. |
| Contestação | A pessoa afetada consegue questionar o resultado? | Canal e procedimento de revisão. |
| Monitoramento | Erros e danos estão sendo acompanhados? | Revisão independente e critérios de interrupção. |

Esses controles são propostas de estudo. Não foram implementados ou avaliados neste trabalho.

## Indicadores candidatos

| Indicador | Cálculo proposto | Limitação |
| --- | --- | --- |
| Proporção de ações indevidas na amostra revisada | Ações consideradas indevidas por revisão independente / ações revisadas | Exige critérios prévios e amostra representativa; não equivale à taxa de falsos positivos do modelo. |
| Decisões com evidência suficiente | Decisões com justificativa e evidências consideradas suficientes / decisões revisadas | Campo preenchido não demonstra qualidade; requer avaliação de conteúdo. |
| Tempo de resolução das contestações | Mediana do intervalo entre abertura e conclusão | Acompanhar casos abertos e qualidade; rapidez isolada pode incentivar encerramentos inadequados. |
| Discordância humana | Decisões diferentes da sugestão automatizada / decisões com sugestão e revisão | Discordar mais ou menos não prova qualidade; deve ser lido com a avaliação independente. |

As métricas precisam de definição de universo, período, critérios e desfechos. Não disponho de dados para calculá-las nem proponho metas numéricas sem baseline.

## Riscos de otimizar uma métrica isoladamente

- Reduzir o tempo de revisão pode incentivar a confirmação automática do alerta.
- Exigir justificativas em todos os casos pode gerar textos padronizados sem análise real.
- Buscar concordância máxima com a IA pode desencorajar discordâncias fundamentadas.
- Buscar discordância máxima pode incentivar decisões contrárias ao sistema sem evidência.

A avaliação proposta combina tempo, fundamentação, ações indevidas e contestação, com revisão independente.

## Limites do estudo

Não houve coleta própria de dados, experimento com agentes, implementação de reconhecimento facial ou medição de resultados. A bibliografia não constitui uma revisão sistemática. Esta nota não atribui experiência técnica em sistemas multiagentes.

## Próximas perguntas

- Como avaliar se uma discordância foi possível, fundamentada e efetivamente considerada?
- Quais decisões precisam de revisão independente antes de uma ação?
- Que dados permitiriam acompanhar erros sem criar novos riscos de privacidade?

As conexões com sociologia dos agentes artificiais e *O Fim da Eternidade*, de Isaac Asimov, poderão ser desenvolvidas em notas próprias. A analogia literária será identificada como interpretação, sem tratá-la como evidência empírica sobre IA.
