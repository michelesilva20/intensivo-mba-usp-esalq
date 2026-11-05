# Simulado misto

Responda às 11 questões, com uma alternativa por questão. Registre suas escolhas antes de consultar o gabarito. Para atingir pelo menos 70%, você precisa de **8 acertos**.

## 1. Estatística descritiva

Cinco tempos de entrega em horas são 2, 3, 4, 5 e 21. Uma auditoria corrige o maior valor para 11. O que acontece?

- A. A média diminui 2 h, a mediana permanece em 4 h e a amplitude diminui 10 h.
- B. A média diminui 10 h, a mediana permanece em 4 h e a amplitude diminui 2 h.
- C. A média e a mediana diminuem 2 h, e a amplitude diminui 10 h.
- D. A média diminui 2 h, a mediana permanece em 4 h e a amplitude permanece igual.

## 2. Probabilidade

A filial Norte realiza 75% das entregas, com taxa de atraso de 4%. A filial Sul realiza 25%, com taxa de atraso de 12%. Sorteou-se uma entrega **entre as atrasadas**. Qual é a probabilidade de ela ser da filial Sul?

- A. 12%
- B. 25%
- C. 50%
- D. 75%

## 3. Clustering

Um agrupamento hierárquico usa distância euclidiana em duas variáveis contínuas, peso em kg e tempo em horas. As escalas diferem bastante e as duas variáveis devem contribuir em uma escala comparável. Com *single linkage*, qual combinação de ações e interpretação faz sentido?

- A. Padronizar as variáveis e usar a maior distância entre pares para unir grupos.
- B. Padronizar as variáveis e usar a menor distância entre pares, que pode formar cadeias.
- C. Manter as escalas e usar a distância entre centroides, evitando encadeamento.
- D. Manter as escalas e escolher o número de grupos por meio do algoritmo K-Means.

## 4. PCA

Uma PCA sobre a matriz de correlação de quatro variáveis tem autovalores 2,10, 1,30, 0,40 e 0,20. Quantos componentes o critério de Kaiser (autovalor acima de 1) retém e que percentual da variância total eles explicam?

- A. Um componente e 52,5%.
- B. Dois componentes e 65%.
- C. Três componentes e 95%.
- D. Dois componentes e 85%.

## 5. Correspondência

Em uma tabela de contingência entre canal e tipo de reclamação, o teste global de independência deu p = 0,01. O resíduo ajustado da célula “telefone × atraso” é +2,7. O que os dois resultados indicam a 5%, usando ±1,96 como referência exploratória por célula?

- A. Há evidência global de associação. Nessa célula, a frequência observada supera a esperada sob independência.
- B. Há evidência global de associação. Nessa célula, a frequência observada fica abaixo da esperada.
- C. O teste global indica evidência insuficiente de associação. O resíduo positivo indica excesso local.
- D. O teste global indica evidência insuficiente de associação. O resíduo mede diretamente a intensidade causal do canal.

## 6. Econometria e séries

Uma regressão logística prevê atraso com logito $\eta=-1{,}6+0{,}8x$, em que $x=1$ indica entrega expressa. Em outra análise, a demanda dos três últimos meses foi 20, 25 e 30. Qual par representa a probabilidade prevista de atraso da entrega expressa e a previsão do próximo mês pela média móvel simples de três períodos?

- A. 69,0% e 25.
- B. 31,0% e 30.
- C. 31,0% e 25.
- D. 44,9% e 25.

## 7. Aprendizado de máquina

A classe positiva é “entrega com avaria”. O modelo acertou 30 positivas e 130 negativas, perdeu 10 avarias e sinalizou 30 cargas intactas. Qual é o *recall* da classe positiva? Em uma Random Forest com *bootstrap*, que observações podem gerar a predição fora da amostra (*OOB*) de uma árvore?

- A. 50%. As observações sorteadas para treinar a árvore.
- B. 75%. As observações que ficaram fora do *bootstrap* daquela árvore.
- C. 81,25%. As observações sorteadas para treinar a árvore.
- D. 80%. Todas as observações usadas para treinar a árvore.

## 8. Risco e finanças

Para uma carteira homogênea, considere probabilidade de inadimplência de 3%, perda de 40% da exposição em caso de inadimplência e exposição de R$ 200.000. No modelo simples de um período, qual é a perda esperada?

- A. R$ 2.400.
- B. R$ 6.000.
- C. R$ 80.000.
- D. R$ 86.000.

## 9. Dados, texto e redes

Você precisa dividir tempos de entrega em quatro faixas de frequências semelhantes e extrair a expressão “não chegou” de comentários mantendo a sequência das palavras. Qual combinação atende ao objetivo?

- A. `pd.cut` com quatro intervalos de largura igual e remoção de “não”.
- B. `pd.qcut` e unigramas sem informação de ordem.
- C. `pd.cut` com quatro intervalos de largura igual e lematização isolada.
- D. `pd.qcut`, verificando empates nos limites, e bigramas que preservem “não chegou”.

## 10. Otimização e simulação

Uma transportadora quer escolher quantos veículos inteiros dos tipos A e B alocar para obter o menor custo total. Cada A custa R$ 300 e transporta 4 t. Cada B custa R$ 450 e transporta 7 t. A carga total deve ser de pelo menos 25 t. Qual formulação representa o problema?

- A. Maximizar $300x+450y$ sujeito a $4x+7y\geq25$, com $x,y$ inteiros não negativos.
- B. Minimizar $300x+450y$ sujeito a $4x+7y\leq25$, com $x,y$ inteiros não negativos.
- C. Minimizar $300x+450y$ sujeito a $4x+7y\geq25$, com $x,y$ inteiros não negativos.
- D. Minimizar $300x+450y$ sujeito a $4x+7y\geq25$, com $x,y$ reais não negativos.

## 11. Gestão e interpretação

O caso diz que as filiais usam definições diferentes de “entrega no prazo”. A direção quer um painel para comparar filiais e uma equipe Scrum para entregar melhorias incrementais. Qual ação responde ao problema de comparação e respeita os papéis do Scrum?

- A. Publicar o painel com as definições atuais e pedir ao Scrum Master que ordene o Product Backlog.
- B. Acordar uma definição comum do indicador e tratar a ordenação do Product Backlog como responsabilidade do Product Owner.
- C. Escolher o tipo de gráfico primeiro e atribuir a ordenação do Product Backlog exclusivamente aos Developers.
- D. Somar os percentuais de prazo de cada filial e entregar ao Scrum Master a responsabilidade de maximizar o valor do produto.
