# Machine Learning

![Resumo visual do tema](resumo.svg)

## Escolha do alvo e avaliação

Classificação prevê categorias, como fraude ou operação regular. Regressão prevê valores numéricos, como prazo de entrega. Separe o conjunto de teste antes da seleção de variáveis e do ajuste de hiperparâmetros. Aprenda imputação, escalonamento e outras transformações usando os dados de treino e aplique as mesmas regras à validação e ao teste. Em dados temporais, preserve a ordem cronológica.

Na classificação binária, declare qual é a classe positiva antes de interpretar a matriz de confusão. Para fraude como classe positiva, um falso negativo é uma fraude classificada como operação regular.

| Métrica | Fórmula | Pergunta respondida |
|---|---|---|
| Acurácia | $(VP+VN)/(VP+VN+FP+FN)$ | Entre todos os registros, quantos foram classificados corretamente? |
| Precisão | $VP/(VP+FP)$ | Entre os alertas, quantos eram fraudes? |
| Recall ou sensibilidade | $VP/(VP+FN)$ | Entre as fraudes reais, quantas foram detectadas? |
| Especificidade | $VN/(VN+FP)$ | Entre as operações regulares, quantas foram classificadas como regulares? |
| F1 | $2cdot(	ext{precisão}cdot	ext{recall})/(	ext{precisão}+	ext{recall})$ | Qual o equilíbrio entre precisão e recall, pela média harmônica? |

**Exemplo.** VP = 30, FN = 10, FP = 20, VN = 140. Acurácia = 85%, precisão = 60%, recall = 75% e especificidade = 87,5%. Se baixar o limiar de alerta, o modelo tende a sinalizar mais operações. O recall pode aumentar e a especificidade pode cair. Com 1% de fraudes, prever tudo como regular dá 99% de acurácia e recall zero.

Em regressão, MAE e RMSE estão na unidade do alvo. RMSE dá mais peso a erros grandes. Uma redução de MAE de 3 para 2 horas em teste indica que o erro absoluto médio caiu uma hora.

## Árvores de decisão

A árvore divide os registros por regras como “distância ≤ 100 km” e produz uma previsão na folha atingida. Em classificação, costuma usar Gini ou entropia para procurar filhos mais homogêneos. Em regressão com critério de erro quadrático, procura reduções na variância dentro dos filhos e prevê a média dos alvos da folha.

**Exemplo.** Um nó com cinco ocorrências e cinco ausências tem Gini $1-(0{,}5^2+0{,}5^2)=0{,}5$. Uma divisão produz duas folhas de cinco registros, nas proporções 4/1 e 1/4. Cada filho tem Gini $1-(0{,}8^2+0{,}2^2)=0{,}32$. A queda ponderada de impureza é $0{,}50-0{,}32=0{,}18$.

- **max_depth** limita a profundidade.
- **min_samples_split** exige um tamanho mínimo no nó para considerar a divisão.
- **min_samples_leaf** exige um tamanho mínimo em cada folha criada.
- **Poda** simplifica uma árvore ao remover divisões pouco úteis segundo um critério de penalização.
- Erro baixo no treino e alto na validação aponta para sobreajuste. Erro alto nos dois pode indicar subajuste.

## Ensemble, bagging, Random Forest e boosting

| Método | Treinamento | Agregação e pista de prova |
|---|---|---|
| Bagging | Treina modelos separadamente em amostras bootstrap, sorteadas com reposição. | Combina por média ou voto. A redução de variância depende da diversidade dos modelos. |
| Random Forest | Combina árvores treinadas com aleatoriedade nos dados e na seleção de variáveis candidatas em cada divisão. | A aleatoriedade ajuda a reduzir a correlação entre árvores. Na forma usual com bootstrap, permite medir desempenho OOB. |
| Boosting | Treina modelos em sequência. Cada etapa busca melhorar o conjunto atual. | AdaBoost dá mais peso a erros anteriores. Gradient boosting ajusta passos na direção que reduz a perda. |
| Votação ou média | Combina previsões de modelos que podem ser de tipos diferentes. | Votação dura usa classes previstas. Votação suave combina probabilidades. Regressão pode usar média. |

**Out-of-bag (OOB)** usa, para cada registro, as árvores cuja amostra bootstrap deixou aquele registro de fora. É uma estimativa interna para modelos com bootstrap. Se a tarefa exige avaliação temporal ou por grupos, use uma separação que reflita essa estrutura.

**Exemplo.** Três classificadores votam A, B, A. Votação dura retorna A. Três modelos de prazo estimam 12, 15 e 21 horas. A média retorna 16 horas. Em gradient boosting com perda quadrática, se o modelo atual prevê 14 e o real é 20, o resíduo é +6. Se a árvore adicionada prevê correção +6 e a taxa de aprendizagem é 0,2, a nova previsão é 15,2.

## Redes neurais e Deep Learning

Um neurônio calcula $z=w^	op x+b$ e aplica uma ativação $a=f(z)$. Camadas ocultas aprendem transformações das entradas. Ativações não lineares permitem representar relações que uma sequência de camadas lineares equivaleria a representar com apenas uma transformação linear.

| Peça | Função |
|---|---|
| ReLU | $max(0,z)$, comum em camadas ocultas. |
| Sigmoide | $1/(1+e^{-z})$, saída entre 0 e 1. Usual na saída de classificação binária. |
| Softmax | Converte um vetor de logits em probabilidades cuja soma é 1. Usual em classes mutuamente exclusivas. |
| Saída linear | Usual para um alvo contínuo sem restrição de faixa. |
| Perda | Quantifica o erro que o treino procura minimizar, como entropia cruzada ou MSE. |
| Retropropagação | Calcula os gradientes da perda por meio das camadas. |
| Otimizador | Atualiza pesos com base nos gradientes. SGD e Adam são exemplos. |

**Exemplo.** Para $x=(2,1)$, $w=(0{,}5,-1)$ e $b=1$, resulta $z=0{,}5cdot2-1cdot1+1=1$. A sigmoide dá aproximadamente 0,731. Com limiar 0,5, a previsão é a classe positiva. Um lote é um grupo de observações processado junto. Uma época corresponde a uma passagem pelo conjunto de treino. Acompanhe a perda em validação. Se a de treino continua caindo e a de validação começa a subir, a parada antecipada pode preservar o ponto de melhor generalização observado.

## Interpretação de prova

- Identifique o tipo de alvo, a classe positiva e o denominador da métrica.
- Para ler uma árvore, percorra as condições da raiz até uma folha e aplique a previsão dessa folha.
- “Amostra com reposição”, “árvores em paralelo” e “OOB” remetem a bagging. “Etapas corrigem o modelo anterior” remete a boosting.
- Reconheça funções comuns de uma interface de modelagem. O ajuste aprende parâmetros, a predição usa o modelo treinado e a avaliação compara as previsões com os alvos. Em Keras, compile configura perda e otimizador, fit treina, evaluate mede desempenho e predict calcula saídas.

## Como os slides ligam técnica e resultado

- **Comparar árvores e ensembles.** Confronte os resultados no mesmo conjunto de avaliação e com a mesma métrica. Em OOB, o conjunto de árvores que prevê cada observação é específico dessa observação.
- **Reconhecer algoritmos pelo mecanismo.** Random Forest combina árvores aleatorizadas. AdaBoost repondera exemplos. Gradient Boosting acrescenta correções à previsão agregada. XGBoost é uma implementação de gradient boosting com regularização e recursos computacionais próprios.
- **Interpretar um output de classificação.** A curva ROC traça sensibilidade contra a taxa de falsos positivos, $1-\text{especificidade}$, ao variar o limiar. A AUC resume a capacidade de ordenação dos positivos e negativos. Para decidir um limiar, observe o custo de alarmes falsos e de casos perdidos.
- **Relacionar tarefa e loss.** Uma rede para prever horas de atraso pode usar saída linear e MSE. Uma rede para sinalizar atraso pode usar saída sigmoide e entropia cruzada binária.


## Checagem rápida

1. Em uma base com 80 fraudes, um modelo acerta 60 delas e gera 15 falsos alarmes. Calcule recall e precisão.
2. Um algoritmo ajusta a segunda árvore à direção que reduz a perda do conjunto atual. Qual é a família?
3. Qual saída combina com três classes mutuamente exclusivas? Qual peça da rede calcula o gradiente?

<details>
<summary>Ver respostas</summary>

1. Recall = 60/80 = 75%. Precisão = 60/75 = 80%.
2. Gradient boosting.
3. Softmax. A retropropagação calcula os gradientes.

</details>

**Material consultado no portal USP/Esalq**

- *Árvores, Redes e Ensemble Models II–III* (01 e 08/09/2026, slides p. 3–42 e 45–46).
- *Deep Learning e IA III* (06/10/2026, slides p. 4–5 e 11).


[scikit-learn · árvores de decisão](https://scikit-learn.org/stable/modules/tree.html) · [Ensembles](https://scikit-learn.org/stable/modules/ensemble.html) · [TensorFlow · treino e avaliação com Keras](https://www.tensorflow.org/guide/keras/training_with_built_in_methods)
