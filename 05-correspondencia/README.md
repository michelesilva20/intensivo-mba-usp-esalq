# Análise de correspondência simples e múltipla

![Resumo visual do tema](resumo.svg)

Use correspondência quando a pergunta for **quais categorias se associam e como representá-las em poucas dimensões**. A análise é exploratória e trabalha com perfis de frequência. A versão simples usa duas variáveis categóricas. A múltipla, três ou mais no contexto do curso. Uma variável quantitativa pode ser categorizada quando as faixas fazem sentido, com perda de detalhe.

## ANACOR — duas variáveis

1. Monte a tabela de contingência com frequências observadas $O_{ij}$, totais marginais $n_{i+}$ e $n_{+j}$ e total $n$.
2. Sob independência, calcule $E_{ij}=n_{i+}n_{+j}/n$.
3. Some $(O-E)^2/E$ para obter $\chi^2$, com $(r-1)(c-1)$ graus de liberdade. Confira independência entre observações e adequação das frequências esperadas. Uma célula rara pode influenciar a análise. Em tabelas pequenas e esparsas, considere um teste exato ou simulado para a etapa inferencial.
4. Para identificar excessos e faltas, leia o sinal dos resíduos. O resíduo de Pearson é $(O-E)/\sqrt E$. O resíduo padronizado ajustado divide $O-E$ por $\sqrt{E(1-n_{i+}/n)(1-n_{+j}/n)}$. Valores ajustados com módulo acima de 1,96 são pistas a 5% em leitura individual aproximada. Ao examinar muitas células, leve em conta a multiplicidade.
5. A análise decompõe a inércia total $\chi^2/n$ em dimensões. Há no máximo $\min(r-1,c-1)$ e a participação de uma dimensão é sua inércia dividida pela total.

**Exemplo.** De 100 entregas, 30 de 50 expressas chegam no prazo, ante 10 de 50 econômicas. A tabela tem linhas (30,20) e (10,40). Em cada linha, a expectativa é (20,30). A célula expressa/no prazo tem resíduo de Pearson $10/\sqrt{20}=2{,}24$ e ajustado $10/\sqrt{20\times0{,}5\times0{,}6}=4{,}08$. O qui-quadrado total é $16{,}67$ e a inércia é $0{,}167$. Há evidência de associação. A tabela sozinha não identifica efeito causal do serviço.

## HOMALS ou ACM — várias variáveis

- Construa uma matriz indicadora com uma linha por observação e uma coluna 0/1 por categoria. Cada bloco de uma variável possui um 1 por observação quando a resposta é única e completa.
- A matriz de Burt é o produto transposto da indicadora por ela mesma. Os blocos fora da diagonal são tabelas cruzadas. Na diagonal ficam os totais de cada categoria.
- A ACM usa um espaço de baixa dimensão para representar padrões conjuntos. Exemplo logístico: modalidade, região e faixa de atraso. Um perfil pode concentrar expresso, capital e prazo cumprido.
- Os autovalores descrevem a inércia por dimensão. Inércia bruta de ACM pode parecer baixa em poucos eixos devido à codificação indicadora. Compare resultados que usam a mesma convenção e confira se o software aplica correção.

## Como ler o mapa

- Comece pela inércia explicada dos eixos e pela qualidade da representação da categoria, frequentemente mostrada como cos². A contribuição responde a outra pergunta, quanto a categoria pesa na construção do eixo.
- Em um mapa de perfis, proximidade entre categorias do **mesmo conjunto** pode indicar perfis semelhantes conforme a escala. Para cruzar pontos de linha e coluna, use a orientação relativa, a convenção de escala e os resíduos da tabela. Distância visual direta entre conjuntos pode enganar.
- Pontos perto da origem tendem a ter perfis próximos da média nos eixos exibidos. Um ponto distante pode ser uma categoria rara, então confira massa e frequência.
- PCA combina variáveis quantitativas e decompõe variância. Correspondência usa frequências categóricas, métrica qui-quadrado e inércia. Clustering tem como objetivo formar grupos de observações.

**Cheque sem consulta.** Na tabela do exemplo, a célula econômica/no prazo ficou acima ou abaixo do esperado? Em uma tabela 3×5, quantos eixos no máximo?

<details><summary>Conferir</summary>

Abaixo, 10 frente a 20. No máximo 2 eixos.

</details>

**Referência do curso**

Aulas de Análise de Correspondência Simples e Múltipla I e II, 13 e 20 de janeiro de 2026, Wilson Tarantin Junior. Material de slides consultado para alinhar a terminologia e os passos.
