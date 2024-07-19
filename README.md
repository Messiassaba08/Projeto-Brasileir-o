# Analise de dados da série A do campeonato brasileiro entre 2013-2023

***** Corrigir cartões por temporada e não ano e corrigir Correlação pontos x Saldos de gols *****



Projeto criado para praticar o uso de Figma, Power BI e Estatística na análise de dados da série A do campeonato brasileiro de futebol de 2013 a 2023.
- Link do Projeto concluído: https://app.powerbi.com/reportEmbed?reportId=c9745383-e81c-4d2a-bb91-61aae2911182&autoAuth=true&ctid=64126139-4352-4cd7-b1fb-2a971c6f69a6
- Link da base de dados: https://www.kaggle.com/datasets/victorhts/brasileiro-srie-a-resultados-2013-2023
- Link do Tutorial de Figma: https://www.youtube.com/watch?v=o5MyY1jCWg8&t=841s
- Link curso gratuito de Power BI: https://www.youtube.com/watch?v=YqH_gTzKZVI&list=PL29iyd7VxXguJm4NiXMKNlh5uNspQsxzv

## Introdução
Esta documentação tem como objetivo principal explicar as decisões voltadas a analise de dados, uso de estatística e da ferramenta de manipulação de dados Power BI. Sendo assim, não irei especificar sobre a criação do dashboard pelo Figma, mas irei deixar o link dos vídeos que usei para auxiliar no uso da ferramenta logo acima. Também deixei o link do curso gratuito de Power BI que realizei para criação do projeto. Lembrando que apenas a visualização dos cursos não irá desenvolver suas habilidades com as ferramentas se não houver prática. Esse é o objetivo da criação desse projeto. :) 

## Estilização
Por se tratar de futebol, optei por realizar a criação do dashboard de forma parecida com os games de futebol. Dessa forma, tive como inspiração de design os jogos FIFA e PES, criando o menu para navegação entre as análises e dentro do menu o histórico de colocação dos clubes em cada ano, podendo filtrar por clube de forma separada. Todo o projeto foi criado do zero, sem utilização de wallpapers ou formas prontas.
 
## Perguntas
Inicialmente, antes de manipularmos os dados, devemos nos perguntar o que queremos extrair dos mesmos. Em uma empresa, na maioria das vezes, teremos questionamentos prontos para solucionarmos com o dataset disponibilizado. Dessa forma, torna-se mais interessante, antes da manipulação, a criação de perguntas para que possamos respondê-las ao longo do projeto. Sendo assim, separei as perguntas em cinco categorias: Cartões Amarelos, Cartões Vermelhos, Gols, Aproveitamento e Campeões.

### Cartões Amarelos:
- Qual a média geral de cartões amarelos por jogo e temporada? Além disso, gostaria de poder comparar a média de cartões geral com a média invidial dos clubes.
- Qual foi o comportamento do número de cartões amarelos ao longo dos anos?
- Existe uma relação forte entre o número de cartões amarelos e o aproveitamento dos clubes?
- Quais os clubes com maior média de cartões amarelos por temporada?
### Cartões Vermelhos:
- Qual a média geral de cartões vermelhos por jogo e temporada? Além disso, gostaria de poder comparar a média de cartões geral com a média invidial dos clubes.
- Qual foi o comportamento do número de cartões vermelhos ao longo dos anos?
- Existe uma relação forte entre o número de cartões amarelos e o número de cartões vermelhos?
- Quais os clubes com maior média de cartões vermelhos por temporada?
### Gols: 
*Observação: Gols contra = tomados pela equipe. Gols pró = Marcados pela equipe.*
- Qual a média geral de gols pró por temporada? Além disso, gostaria de poder comparar a média de gols pró geral com a média invidial dos clubes.
- Qual a média geral de gols contra por temporada? Além disso, gostaria de poder comparar a média de gols contra geral com a média invidial dos clubes.
- Qual a relação entre Pontos e Saldo de Gols?
- Qual a relação entre Posição e Saldo de Gols?
- Quais os clubes com maior média de gols por temporada?
### Aproveitamento:
- Quais times disputaram mais temporadas?
- Qual a média de aproveitamento por estado?
- Quais times tiveram maior aproveitamento médio por temporada
### Campeões:
- Gostaria de visualizar a soma de todos os dados em uma única tabela
- Quais times fizeram mais pontos ao longo de todas temporadas?
- Quais foram os campeões e quantos títulos tiveram cada um?

## Tratamento dos dados
O Primeiro passo após baixar a tabela com os dados no site Kaggle(Link da base de dados no início da documentação), foi transformar os dados dentro do Power BI. Os dados, em formato .csv, foram formatados separados apenas por vírgula.
![image](https://github.com/user-attachments/assets/1d404939-9d04-4e82-b7e8-26066e19c80c)

Ao subir no Power BI, selecionei a opção de criar colunas e escolhi a vírgula como separador, tendo esse resultado:
![image](https://github.com/user-attachments/assets/9d6e4328-3f61-488f-8540-7f80e15f0de0)

Após isso, revisei os tipos e modifiquei a maioria de caraceteres para inteiros, com o objetivo de facilitar a realização de cálculos e criação de gráficos. Além disso, achei um erro, no qual, os clubes Atlético Mineiro e Athletico Paranaense estavam com o mesmo nome "Atlético", então mesclei as colunas "Time" e "UF" mas antes criei uma cópia de UF para utilizar em futuros cálculos. Depois, revisei os dados e segui para a criação das métricas e gráficos. Mais tarde, percebi que o América Futebol Clube estava sendo representado de duas formas: América e America, em
## Como foram respondidas as perguntas
### Cartões Amarelos:
#### Qual a média geral de cartões amarelos por jogo e temporada? Além disso, gostaria de poder comparar a média de cartões geral com a média invidial dos clubes.
Criei uma nova tabela apenas para colocar todas as novas medidas que irão ser criadas. Após isso, criei a medida média de cartões amarelos utilizando o seguinte código:

![df](https://github.com/user-attachments/assets/a8ba6131-58bd-407d-8348-96d73ebdd3e8)

Este código DAX calcula a média dos cartões amarelos por ano. Ele faz isso iterando por cada ano distinto presente na coluna 'BrasileiraoBase'[Ano] e, para cada ano, calcula a média dos cartões amarelos ('BrasileiraoBase'[Cartões Amarelos]) nesse ano. Finalmente, ele calcula a média desses valores resultantes.
Resumidamente, calcula a média das médias anuais. Eu poderia ter feito a média de muitas formas, por exemplo, somando todos os cartões amarelos e dividindo pelo número de temporadas ou utilizando medianas. Porém, nesse caso, a média das médias é mais acertivo por não ser tão sensível aos anos atípicos e, ao mesmo tempo, não anular totalmente os outliers. Esse lógica será usada para a maioria dos casos desse projeto.
Além disso, para a comparar a média geral e individual, criei cartões com a mesma fórmula, porém, pode-se aplicar filtros de clubes neles.
#### Qual foi o comportamento do número de cartões amarelos ao longo dos anos?
Pensando na melhor visualização ao longo do tempo, foi utilizado o gráfico de linhas.
#### Existe uma relação forte entre o número de cartões amarelos e o aproveitamento dos clubes?
Para análise de relação entre uma variável e outra utilizei o gráfico de dispersão, usando correlação e traçando a linha de tendência para uma possível regressão linear.
#### Quais os clubes com maior média de cartões amarelos por temporada?
Utilizei o gráfico de barras para esta análise com o objetivo de evidenciar os maiores números e, ao mesmo tempo, permitir a analise de todos os clubes.
### Cartões Vermelhos:
Usada a mesma lógica que os cartões amarelos
### Gols: 
#### 4 primeiras perguntas 
utilizamos a mesma lógica das anteriores
#### Quais os clubes com maior média de gols por temporada?
Dessa vez, preferi usar o Treemap. Nele, podemos ter uma visualização geral de todos os clubes sem precisar movimentar o gráfico.
### Aproveitamento:
#### Quais times disputaram mais temporadas?
Criei a medida Temporadas Disputadas = CALCULATE(COUNT('BrasileiraoBase'[Ano]))
Ela soma o número de vezes que o ano aparece junto a outra coluna que no caso será o time. Poderia ter usado COUNTDISTINCT, porém, nesse caso, não há diferença, tendo em vista que temos apenas uma linha no máximo por time em cada ano.
#### outras 2 perguntas utilizei a mesmo lógica das anteiores
### Campeões:
#### Gostaria de visualizar a soma de todos os dados em uma única tabela
 Criei gráfico tabela e adicionei as colunas do gráfico padrão da CBF
Quais times fizeram mais pontos ao longo de todas temporadas?
Representei pelo gráfico de barras para dar mais ênfase a diferença das equipes
#### Quais foram os campeões e quantos títulos tiveram cada um?
Como são poucos clubes, utilizei o gráfico rosca que nos dá toda informação de forma proporcional.

## Análise dos Dados
### Cartões Amarelos

![card](https://github.com/user-attachments/assets/ac90ca77-88d0-4997-ae5c-830b91c31029)

Observa-se, por meio do gráfico de linhas cartões amarelo x ano, uma tendência de crescimento do número de cartões amarelos ao longo dos anos. O número de cartões é proporcional ao número de faltas que é proporcional ao tempo de paralisação dos jogos. Dessa forma, percebe-se que deveria haver mudançar em relação ao tempo de jogo. Percebemos essa mudança após a copa de 2022 com o aumento do número de acréscimos em todo o mundo, seguindo o padrão da copa. Além disso, entende-se que houve um aumento do rigor por parte dos árbitros ou maior indisciplina por parte dos times, o que seria melhor avaliado em dados mais aprofundados.

![dv](https://github.com/user-attachments/assets/814c5a94-8899-4b1a-b2fb-90c8a4fd401b)

Uma linha de tendência horizontal sugere que, dentro do intervalo de dados observados, não há uma relação linear perceptível entre as variáveis representadas no gráfico de dispersão. Nesse sentido, entende-se que a quantidade de cartões amarelos não tem impacto no aproveitamento das equipes.

### Cartões Vermelhos



## Conclusão
