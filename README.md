# Walmart

* *Wallmart é uma corporação de varejo que opera como uma rede de supermercados.*
* *Temos os dados de 45 lojas  no período de 2010-02-05 á 2012-11-1.*
* *Existem em cada loja 99 departamentos.*
* *Também temos os dados de vendas semanais em cada loja/departamento.*
* *Devemos considerar ainda que o Walmart tem uma política de promoções ao longo do ano, principalmente em datas que precedem feriados importantes.*
 
**Esse notebook tem como objetivos apresentar as seguintes análises:**

1. Qual é o impacto dos feriados (promoções também) nas vendas das lojas?

2. Existe algum setor que desempenhe melhor?

3. É possível estimar as vendas das lojas por semana em datas futuras de 2012–11–02 a 2013–07-26? Se sim, quais seriam esses valores?

## Informações Técnicas:

O dataset Walmart está disponível no [Kaggle]( https://www.kaggle.com/competitions/walmart-retail-case-study2/data) e possui as seguintes características:

* Store - the store number (código da loja)
* Date - the week of sales (semanas de vendas)
* Weekly_Sales - sales for the given store (vendas por loja)
* Holiday_Flag - whether the week is a special holiday week 1 – Holiday week 0 – Non-holiday week (se a semana é um feriado especial semana 1 – Semana de feriado 0 – Semana sem feriado)
* Temperature - Temperature on the day of sale (temperatura do dia da venda)
* Fuel_Price - Cost of fuel in the region (Preço total na região)
* CPI – Prevailing consumer price index (Índice de preços ao consumidor)
* Unemployment - Prevailing unemployment rate (taxa de desemprego)

## Conclusão: 

### 1. Qual é o impacto dos feriados (promoções também) nas vendas das lojas?

Para verificar o impacto dos feriados optei por começar vendo as correlações.
A correlação é uma análise que mede a força de associação entre duas variáveis.  Em termos da força da relação, o valor do coeficiente de correlação varia entre +1 e -1.  Um valor de ± 1 indica um grau de associação perfeito entre as duas variáveis.  Como o valor do coeficiente de correlação vai para 0, a relação entre as duas variáveis será mais fraca.  A direção da relação é indicada pelo sinal do coeficiente; um sinal + indica uma relação positiva e um sinal – indica uma relação negativa.

Para fazer essa análise medi três tipos de correlações: 


* Correlação de Spearman

<img src ="https://user-images.githubusercontent.com/79377636/209346682-9aac0224-713d-462b-8d82-850bd7d4d524.png"
     height = "250px"/>

* Correlação de Pearson

<img src ="https://user-images.githubusercontent.com/79377636/209346853-223a50e7-0103-40fa-9ddf-0b89e94a4da7.png"
     height = "250px"/>

* Correlação de Kendall

<img src ="https://user-images.githubusercontent.com/79377636/209346995-870e5f54-534b-4719-b6b9-add26dbc618b.png"
     height = "250px"/>
     
Com essa análise podemos ver que as três formas de medir correlação ficaram próximo de 0 o que indica uma relação fraca entre feriados e vendas das semanas.

#### Comparando as vendas com e sem feriado

<img src ="https://user-images.githubusercontent.com/79377636/209347540-07f52676-09e4-4eaf-a830-4deb7d77f794.png"
     height = "200px"/>
     
Com esse gráfico é possível verificar que as vezes o efeito do feriado é positivo, entretanto não é um comportamento padrão, pois a pontos em que o feriado está inferior ao dia normal

#### Analisando especificamente cada feriado

<img src ="https://user-images.githubusercontent.com/79377636/209346144-ed6652c7-5a07-4b4a-a675-367ba92bf8e3.png"
     height = "200px"/>
<img src ="https://user-images.githubusercontent.com/79377636/209346154-5dca18e7-6a88-471f-8dbb-57b519aaa76d.png"
     height = "200px"/>
<img src ="https://user-images.githubusercontent.com/79377636/209346158-9b8a2104-884a-448b-b006-047f71d2cd93.png"
     height = "200px"/>
     
A partir dos gráficos acima, podemos inferir que Labor Day não a aumento das vendas, assim o feriado podemos concluir que este feriado não tem forte impacto nas vendas.
Já em Thanksgiving, podemos observar uma grande diferença no número de vendas, desta maneira um impacto positivo dos feriados nas vendas semanais. 
Diferentemente ao Christmas, em que há uma pequena diferença nas vendas de forma negativa, resultado que indica um comportamento de compra antecipada dos consumidores.


### 2. Existe algum setor que desempenhe melhor?

![Group 7](https://user-images.githubusercontent.com/79377636/209347379-867076f7-5901-4951-957f-8f2b62f5c809.png)
A partir do gráfico verifica-se que o departamento 92 tem uma média de vendas superior.

### 3. É possível estimar as vendas das lojas por semana em datas futuras de 2012–11–02 a 2013–07-26? Se sim, quais seriam esses valores?


Sim é possível, análise de séries temporais tentar estudar o comportamento dos dados, ao longo do tempo, de forma a compreender a estrutura que gerou a série. 
Para isso irei utilizar a ferramenta Prophet que permite gerar previsões e cenários futuros para séries temporais.
Com ela cheguei no seguinte resultado:

![previsao_q3](https://user-images.githubusercontent.com/79377636/209345505-f7d7f354-fb14-4f24-8e8b-5593d025f8a3.png)

![tendencia_q3](https://user-images.githubusercontent.com/79377636/209345614-0d2963d6-d25e-4b3f-bf75-5b531dfe0c0e.png)

Esse resultado encontrado permite ver a tendência de crescimento ao longo do tempo, bem como possíveis numero de vendas para as próximas datas.

