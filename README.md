# Analise de dados da série A do campeonato brasileiro entre 2013-2023

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
utilizamos a mesma lógica das anteriores. Cada ponto representa o saldo de gols e aproveitamento separador por time e ano, ou seja, para o flamengo que disputou 11 temporadas existem 11 pontos. Dessa forma, teremos uma maior quantidade de dados e o os valores terão uma proporção real, nesse exemplo, de aproveitamento x saldo de gols.
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
Fonte: https://ge.globo.com/espiao-estatistico/noticia/2023/05/02/brasileirao-inicia-com-aumento-de-56percent-nos-acrescimos-veja-balanco.ghtml

![dv](https://github.com/user-attachments/assets/814c5a94-8899-4b1a-b2fb-90c8a4fd401b)

Uma linha de tendência quase horizontal, mas tendendo para baixo, sugere que há uma pequena relação negativa entre as variáveis representadas no gráfico de dispersão. À medida que os valores da variável no eixo X aumentam, os valores da variável no eixo Y diminuem um pouco, mas essa relação não é muito forte.

### Cartões Vermelhos

![cva](https://github.com/user-attachments/assets/ce79d04b-1638-4ae4-b899-d468e75adb56)

Percebe-se um leve aumento do número de cartões vermelhos, não tão expressivo quando o número de cartões amarelos, mas devemos levar em consideração que a incidência de cartões vermelhos é menor.

![correcvca](https://github.com/user-attachments/assets/ea4e23bd-0e39-438c-b453-176da37bbc84)

A correlação entre cartões amarelos e vermelhos segue uma linha de tendência levemente inclinada para cima, indicando que pode haver influência, mas que não há um grande nível de significância.

### Gols

![cvcv](https://github.com/user-attachments/assets/1ab421c1-9a16-4ac2-a0ad-3460090d0610) 

Percebe-se uma forte coreelação entre o saldo de gols e aproveitamento, podendo aplicar a regressão linear para previsão de um possível aproveitamento ou saldo de gols por meio da linha de tendência.

![cvcvcvc](https://github.com/user-attachments/assets/6bed8234-639a-4982-857e-23516efa5c6d)

Apesar disso, o que mais me chamou atenção foi o fato do saldo de gols afetar diretamente o aproveitamento e não possuir o mesmo nível de correlação entre a posição final na tabela. Conseguimos perceber isso por meio da disposição dos dados. Na figura do aproveitamento, percebemos uma maior proximidade dos pontos, representados pelos dados, e no gráfico de posição dados mais espalhados, representando um número maior de erro em relação a linha de tendência. Isso indica que o saldo de gols tem maior influência no aproveitamente do que na posição final na tabale, além do gráfico de posição ter erro de previsão maior. Isso ocorre devido ao fato de que o seu aproveitamento depende somente do seu desempenho, enquanto a posição depende, também, do desempenho de outras equipes.

### Aproveitamento

![apr1](https://github.com/user-attachments/assets/6dfc394e-85ad-40d0-8595-4d6df94a8a68)

No treemap, observamos quais times tiveram o maior e pior desempenho nos últimos 11 anos. Ele é a média das médias dos aproveitamento por temporada, ou seja, mesmo que um time tenha jogado menos temporadas que outros, continua sendo justo em sua métrica. Além disso, ele possibilita fazer a filtragem dos clubes e comparar com a média de seus estados.

![pr fla](https://github.com/user-attachments/assets/b20e3e9a-6b94-4c0b-a154-50a09bd6560b)

Filtrando: Flamengo

![pr vasco](https://github.com/user-attachments/assets/97570e77-e113-4266-a304-2a6c614fd58b)

Filtrando: Vasco

![temp](https://github.com/user-attachments/assets/2a9b3e3f-186e-4b1e-a612-5a8801be0791)

O gráfico acima permite perceber quais times jogaram todas as temporadas de 2013 até 2023 e se não jogaram, quantas jogaram. Percebe-se então que as 7 primeiras posições permanesceram na serie A durante todos esses anos.

![apr 11](https://github.com/user-attachments/assets/c54fccec-4bc4-43b9-b402-b7655eb011d5)

A média de aproveitamento por estado é um excelente parâmetro para medir o desempenho dos times por estado e fazer uma análise temporal:

![pr 2017](https://github.com/user-attachments/assets/9c8c05af-9c28-4cda-9842-bc8f96ca03e0)

2013 - 2017

![pr 2021](https://github.com/user-attachments/assets/617c9a2f-e216-42ff-ba80-b1752059fcde)

2013 - 2021

![pr 2023](https://github.com/user-attachments/assets/b6a0186c-cc48-4f6c-9d0a-fc2c8c01bac1)

2013 - 2023

Nota-se um aumento do desempenho de clubes Paulistas e Cariocas ao longo do tempo e diminuição de clubes Mineiros.

### Campeões

![camp](https://github.com/user-attachments/assets/94f0b9a7-40db-43d3-a1a8-3b1f329209e2)

Gráfico de simples entendimento indicando o número de títulos por time. Palmeiras se destacando.

![tab](https://github.com/user-attachments/assets/908e1e60-8629-4609-bd02-62c157e6a86a)

O objetivo principal da criação dessa tabela foi mostrar como seria se o campeonato fosse disputado sem divisão de temporadas durante esses 11 anos. Nesse caso, podemos observar que o Flamengo seria o campeão pelo número de pontos. Trata-se de uma comparação injusta devido a não utilização de, por exemplo, medidas de tendência central, tendo em vista que o Flamengo só poderia ser comparado com times que permanesceram a mesma quantidade de temporadas na séria A. Ainda assim, a visualização por meio de tabela pode trazer insights em uma vizualização de dados, principalmente, conectadas a filtros. Por exemplo, o fato do Fluminense ter um grande número de cartões amarelos, vermelhos e derrotas comparado a outros times que também disputaram 11 temporadas e o saldo de gols do Palmeiras ser superior ao Flamengo, indicando que, apesar de fazer muitos gols, o Flamengo também toma muitos gols.


## Conclusão

Dessa forma, percebe-se como a análise de dados é importante para a tomada de decisões e a importância de entender muito bem a base da estatística e aliar junto a ferramentas para obter insights significativos em seus projetos e empresas.
